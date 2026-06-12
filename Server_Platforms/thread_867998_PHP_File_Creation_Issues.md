---
title: "PHP File Creation Issues"
date: 2008-07-23
forum: Server Platforms
---

### Post by darkorical on 2008-07-23
Alright I'm back with another round of troubles.

Im building a system to attach notes to orders and have this lovely chunk of code
```
<?php 
error_reporting(0);
$note=$_POST['note'];
$q=$_POST['q']; //cust num
$w=$_POST['w']; //po
$r=$_POST['r']; //rep
$s=$_GET['s']; //cust num
$t=$_GET['t']; //po
$u=$_GET['u']; //rep
echo'
<html>
 <head>
  <title>Add Note</title>
 </head>
  <body bgcolor="#C1C2D5">
<form action="note.php" method="post">
<table border="1" width="90%" align="center">
	<tr>
		<td width="24%"align="center">Rep Name:<br><input type="text" name="r" id="r" value="'.$r.$u.'"></td>
		<td width="25%" align="center">Customer Number:<br><input type="text" name="q" id="q" value="'.$q.$s.'"></td>
		<td width="25%" align="center">PO#:<br><input type="text" name="w" id="w" value="'.$w.$t.'"></td>
		<td width="25%" align="center"><input type="button" value="Reload page" onclick="reloadPage()" /></td>
	</tr><tr>
		<td colspan="3" align="center"><textarea name="note" cols="65" rows="30"></textarea></td>
		<td rowspan="2"><iframe name="dnot" frameborder="0" id="dnot" src="./orders/'.$q.$s.'/'.$w.$t.'/notes.html" width="400" height="525">Something has gone terribly wrong call for help</iframe></td>
	</tr><tr>
		<td colspan="3" align="center"><input name="Save" type="submit" value="Save" /></td>
	</tr>
</table>';
$format="%m/%d/%Y %H:%M:%S";
$strf=strftime($format);
$form = '********************************************<br>'.$r .' -- '. $strf.'<br><br>'.$note.'<br>';
mkdir('./orders/'.$q, 0777);
sleep(1);
mkdir('./orders/'.$q.'/'.$w, 0777);
sleep(1);
$myFile ='./orders/'.$q.'/'.$w.'/notes.html';
$fh = fopen($myFile, 'a') or die("can't open file");
fwrite($fh, $form);
fclose($fh);
?>
```
long story short it takes entered data and saves it in a specific place and then appends to the end of that file any time another note is made 

this works just fine on a local test machine running WAMP but when it goes on my LAMP it can create the file but not write to it again later as upon creation it is chmoded to 644 and the owner is set to root 

where do I go to set it so the file is chmoded to 777  upon creation or what do I need to put in my code to do this 
I already tried chown($myfile, "www-data") and chmod($myfile,0777) both failed to work through the script but making the changes by hand made the script work just fine but as I expect no less than 100 notes a day I really dont want to have to chmod them by hand. any help would be appreciated.

also tried fopen($myFile, 'a+')

---

### Post by Endwin on 2008-07-23
It looks like it is a permissions issue. I would make sure that all the files and the directory that the files run in are owned by the web server, in Ubuntu this is www-data. What is odd is that files made are defaulting to root which makes me think that the owner of the directory is root, and thus is the primary source of the problem. Whenever the web server tries to write, read, or modify files (permissions included) it does not have the power to do so.

What I would do is go to the parent directory and run the command.

```
chown -R www-data:www-data <DIRECTORY>
```

That will make the directory where the file runs, and all data/directories in there to be owned by the web server. Hopefully this will let your script work.

---

### Post by windependence on 2008-07-23
Do you REALLY want all your files world writable/readable?

-Tim

---

### Post by darkorical on 2008-07-23
> **windependence said:**
> Do you REALLY want all your files world writable/readable?

-Tim
Actually yes I do I am making a Customer Service and order information system for in house use only our customer service people will need to be able to make notes on accounts and orders. to do this I have used the preceding code I want it to be set up such that they can always add to it but using a+ they can never delete things from it. (and no offense to my work place but I don't think anyone here poses much of a threat to my linux box as most of them struggle to use the windows machines we give them.

unfortunately the suggestion of the ownership did not fix my issue I can now modify existing files but not the new ones I create any other suggestions?

---

### Post by Endwin on 2008-07-23
It would be useful to see an ls -la of the directory this is running in and the parent directory, and the name of the directory where the scripts are being run.  Might shed some light on why the command I suggested did not work.

Also I wonder if the directories being made by mkdir are being owned by the correct user. For example for some reason when you create the directories and then the file it is setting the user/owner to root:root or something else. We want it to be www-data:www-data which is what the web server is.

I would check your PHP.ini file maybe that could shed some light on who the owner and group creation default is. You should set this to the same as the web server. 

I take it you have full control of the server, running ubuntu, and installed PHP and apache through the package managers?

---

### Post by darkorical on 2008-07-24
alright the directory structure is as follows var/www/artcard/orders/(customernumber)/(PONumber)/  var and www are both root:root. artcard and  everything else in www is owned by me (dan) orders is owned by www-data it is a mounted windows shared file from our other server. I set the entire contence of the directory to www-data: www-data. However all files and folders are being created as root:root not www-data if I change the owner by hand it works just fine 
there are 5000 folders 1 for each customer in orders and about 500 random files that people are being reprimanded for putting in there as well

I looked in PHP.ini but im not sure what exactly to look for  a search for file or folder creation didnt show anything nor did owner or a direct look for root any further advice on where to look in there.

yes I have full control over the machine I use webmin and ssh for managing it.

---

### Post by mbeach on 2008-07-24
how do you mount the windows share?  are you using fstab for that, using which user?  perhaps a credentials file or username=www-data, and create a www-data user on the windows box.  Alternatively, I'd look at the permissions setup on the windows box - from the ubuntu command line, create a file in orders as root, then save it then alter it (still as root) - does it save ok on the subsequent altering?

It appears you have settled on using the filesystem for these notes, and perhaps there is a requirement for that particular structure (other software already uses it etc), however, I'd start looking at using a database for this, because it's only a matter of time before some manager is going to ask for some nifty reporting which will be tough with the file system structuring the data in this way (just my $0.02).  Eventually someone else will say, can't these look better - then you'll be stuck coming up with some way to batch edit all those notes.html files.  Sorry for the rant - just I've been that guy that had to do the eventual cleanup (random files as you already have), and subsequent conversion to a db.

---

### Post by mbeach on 2008-07-24
similar issue before:
[http://ubuntuforums.org/archive/index.php/t-641326.html](http://ubuntuforums.org/archive/index.php/t-641326.html)
but without the windows share complexity

you might get some mileage out 29 Jun 2006 9:28pm UTC (currently last) post at:
[http://bugs.php.net/bug.php?id=37946](http://bugs.php.net/bug.php?id=37946)

---

