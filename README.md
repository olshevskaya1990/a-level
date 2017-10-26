<?php
$write=fopen('W:\myprogram\03\write.txt', "w+");
fclose($write);
$allfile=fopen('W:\myprogram\03\fizz.txt', "r");

if ($allfile) 
{
	while (!feof($allfile)) 
	{
		$line=full_trim(fgets($allfile));
		//echo $line;
		$array=explode(" ",$line);
		//echo $array[0]." ".$array[1]." ".$array[2]."\n";
		fizz_buzz($array[0],$array[1],$array[2]);
	}
}
fclose ($allfile);

function fizz_buzz($a,$b,$c) {
	$writetofile=fopen('W:\myprogram\03\write.txt', "a+");
	$fb_str="FB ";
	$f_str="F ";
	$b_str="B ";
	$i=1;
	while ($i<=$c) {
   	 if (($i%$a==0)&&($i%$b==0)) {
   	    echo $fb_str;
   	    fwrite($writetofile,$fb_str);
   	}
   	 elseif ($i%$a==0) {
   	 	echo $f_str;
   	 	fwrite($writetofile,$f_str);
    }
   	 elseif ($i%$b==0) {
        echo $b_str;
        fwrite($writetofile,$b_str);
    }
   	 else {
   	 	echo "$i ";
   	 	fwrite($writetofile,$i." ");
   	}
	$i++;
	}
	echo "\n\n";
	fwrite($writetofile,PHP_EOL.PHP_EOL);
	fclose($writetofile);
}
function full_trim($str)                             
{                                                    
    return trim(preg_replace('/\s\s+/', ' ', $str));
                                                      
}
