---
title: "WAMP to LAMP Upgrade: PHP Scripts Will Not Run"
date: 2009-10-18
forum: Server Platforms
---

### Post by JRWoodwardMSW on 2009-10-18
I had developed several php scripts in WAMP (a Windows solution stack that combines Apache, MySQL and PHP) and I wanted to put them on my new Ubuntu computer so I could finish them. They will be hosted on a Linux box, and anyway I am phasing Windows out of my life for good. I got the two sites configured under Apache. The first site has an index.htm page and the second has index.php. The first page uses AJAX -- Javascript scripts that start PHP scripts by sending them a URL. The second page is mostly PHP. The AJAX scripts in the first page can't run theirPHP scripts and a little embedded PHP I put in for a test doesn't run, either. (The test was <? php echo "Running"; ?>) The second page does not display. I get the error message below:

**Parse error**:  syntax error, unexpected T_STRING in **/var/www/FRA_DE/index.php** on line **1**

Here is line 1, nd some of the following lines:

&#65279;<?xml version="1.0" encoding="UTF-8"?> 
<!DOCTYPE html  
     PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" 
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> 
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 
     
     
<head> 
<title>Federal Register Activism -- DATA ENTRY PAGE</title> 
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
<link href="css/fra.css" rel="stylesheet" type="text/css" />

As you can see, it's just an html header. The first actual PHP begins on line 55:

       <?php  
           require_once('/var/www/FRA_DE/lib/add_entry.php');  
             #format_date function 
             # This function converts dates to and from MySQL native format. Courtesy of "Josue R.";  
             # posted by him at [http://us2.php.net/manual/en/function.strftime.php](http://us2.php.net/manual/en/function.strftime.php) 
                function format_date($original='', $format="%m/%d/%Y") {  
                        $format = ($format=='date' ? "%m-%d-%Y" : $format);  
                        $format = ($format=='datetime' ? "%m-%d-%Y %H:%M:%S" : $format);  
                        $format = ($format=='mysql-date' ? "%Y-%m-%d" : $format);  
                        $format = ($format=='mysql-datetime' ? "%Y-%m-%d %H:%M:%S" : $format);  
                    return (!empty($original) ? strftime($format, strtotime($original)) : "" );  
                }  
             #be preparted to process queries so that dynamic menus can be built     
 
            function choicemaker($table, $col_name, $purpose, $row_length)    

My WAMP PHP version was 5.2.9 and my Apapche version was 2.2.11
My Ubuntu PHP version is 5.2.2-4 and my Apache is 2.2.8

I already did the chmod command to make index.php executable. Javascripts fun, including scripts stored in an external file in another folder. The Apache access.log shows the access, but the error log shows nothing. I am using only the default logging.

Any ideas? Anyone?

---

### Post by ikt on 2009-10-18
[http://answers.yahoo.com/question/index?qid=20070527201730AAf3bJd](http://answers.yahoo.com/question/index?qid=20070527201730AAf3bJd)

?

---

### Post by JRWoodwardMSW on 2009-10-18
I tried that. I'm surprised that the W3C validated the code with that error, but it didn't fix my problem. The fix in the Yahoo Answers page may have been something particular to Zend, which I am not using. Thanks for trying!

---

### Post by CyberJack on 2009-10-20
What error do you get when removing the '<?xml version="1.0" encoding="UTF-8"?>' line?
The original error indicates that php does not understand <?xml and removing the line should solve your problem.

The reason W3C validates it is because the code is valid xhtml.
So if you need the first line, a possible solution would be echoing the first line with php.
That way php does not try to parse the first line:
[PHP]
<?php
echo '<?xml version="1.0" encoding="UTF-8"?>';
?>
<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head> 
...
[/PHP]

---

