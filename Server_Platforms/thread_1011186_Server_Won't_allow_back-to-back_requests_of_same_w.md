---
title: "Server Won't allow back-to-back requests of same web site"
date: 2008-12-14
forum: Server Platforms
---

### Post by secondstage on 2008-12-14
I can access thewebsite.com/a/ once, but if I try again, it redirects me to thewebsite.com. It doesn't do that for any other page.

PS. thewebsite.com/a/ is a PHP web site (if that has anything to do with it).

---

### Post by secondstage on 2008-12-14
I've done some testing, and come to the conclusion that it must been in the script. The web site is hosted locally, so localhost somehow redirected it to the domain name. Moving the file around made no difference. Changing permissions: Nothing. 

Here is the script...
[PHP]<?php


$_username = $_COOKIE['username'];
$_toWhere = $_SERVER['QUERY_STRING'];

//start the session
session_start();

//check to make sure the session variable is registered
if (session_is_registered($_username)){
setcookie('username', "$_username", time()+3600, '/');



if($_toWhere == '') {
	print '
	<html>
	<head>
	<title>Attritional Times INC.: the Blog</title>
	<link rel="stylesheet" href="../style.css" type="text/css">
	<script language="JavaScript">
	function preloader() {
		// counter
		var i = 0;
		// create object
		imageObj = new Image();
		// set image list
		images = new Array();
		images[0]="image/indi/indiXXSMLR5.png"
		images[1]="image/indi/indiXXSMLL5.png"
		images[2]="image/mult/multXXSMLR5.png"
		images[3]="image/mult/multXXSMLL5.png"
		images[4]="image/edit/editXXSMLR5.png"
		images[5]="image/edit/editXXSMLL5.png"
		// start preloading
		for(i=0; i<=5; i++) {
			imageObj.src=images[i];
		}
	}
	var tt=null;
	function roll(img_name, img_src) {
		document[img_name].src = img_src;
		if(tt!=null)
		 clearTimeout(tt);
	}
	function onOUT(imgSRC0, imgSRC1, imgNAME) {
		roll(imgNAME, imgSRC0);
		tt=setTimeout("roll(\'"+imgNAME+"\'\, \'"+imgSRC1+"\');", 250);
	}
	window.onunload=function()
	{
	 window.location="../logout.php";
	}
	</script>
	</head>
	<body>
	<div align="center">
	<div align="center" class="banner"><a href="../choose.php"><img src="../banner.gif" alt="Attrional Times INC." class="banner"/></a><img src="../blogLogo.png" alt="Blog" class="banner"/></div>
	<br />
	<div align="center">
	<table>
	<tr>
		<td>
			<a href="http://xxx.xxx.xxx.xxx/blog/?yours" onmouseover="roll(\'one\', \'image/indi/indiXXSMLR5.png\')" onmouseout="onOUT(\'image/indi/indiXXSMLL5.png\',\'image/indi/indiXXSML.png\', \'one\')"><img src="image/indi/indiXXSML.png" alt="View Your Blog" name="one"/></a>
			<br />
			<p align="center"><b>View Your Blog</b></p>
		</td>
		<td>
			<a href="http://xxx.xxx.xxx.xxx/blog/?others" onmouseover="roll(\'two\', \'image/mult/multiXXSMLR5.png\')" onmouseout="onOUT(\'image/mult/multiXXSMLL5.png\',\'image/mult/multiXXSML.png\', \'two\')"><img src="image/mult/multiXXSML.png" alt="View Other Peoples\' Blog" name="two"/></a>
			<br />
			<p align="center"><b>View Other People\'s Blogs</b></p>
		</td>
		<td>
			<a href="http://xxx.xxx.xxx.xxx/blog/?edit" onmouseover="roll(\'three\', \'image/edit/editXXSMLR5.png\')" onmouseout="onOUT(\'image/edit/editXXSMLL5.png\',\'image/edit/editXXSML.png\', \'three\')"><img src="image/edit/editXXSML.png" alt="Edit Your Blog" name="three"/></a>
			<br />
			<p align="center"><b>Edit Your Blog</b></p>
		</td>
	</tr>
	<table>
	</div>
	<table class="all">
	<tr><td>
	<!--this page takes the user input and \'posts\' the data as numbers and strings so that the save.php file can check to data, and submit it into a mysql database.-->
	<div align="center"><br />
	</div>
	<table>
	<tr>
	<td width="100%">
	</td>
	</tr>
	<tr>
	<td width="100%">
	<div align="center">
	<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;You have Three options at this point: View your blog, View someone else\'s blog, or Edit your own. Just click the corresponding button. Make sure that you agree with the <a href="http://xxx.xxx.xxx.xxx/text/terms/">Terms of Use</a>.</p>
	</div>
	</td>
	</tr>
	</table>
	<br />
	<sub vertical-align="bottom"><sub><sub>The Blog a completely free service. The Owner of this site, Attritional Times INC., has to right to stop displaying any and all blogs, at any point in time. Attritional Times INC. is also not responsible for (1) any lose of relationships because of blog posts and (2) the suspension of students of any school because of the use of content of posts.</sub></sub></sub>
	</td></tr>
	</table>
	</div>
	</body>
	</html>';


} elseif($_toWhere == 'yours') {
	
	
	print 'N/A';
	
	
} elseif($_toWhere == 'others') {
	$_width = 1;
	print '<html>
	<head>
	<title>Attritional Times INC.: the Blog</title>
	<link rel="stylesheet" href="../style.css" type="text/css">
	</head>
	<body>
	<div align="center">
	<div align="center" class="banner"><a href="../choose.php"><img src="../banner.gif" alt="Attrional Times INC." class="banner"/></a><img src="../blogLogo.png" alt= Blog" class="banner"/></div>
	<table class="all">
	<tr><td><br />';
	mysql_connect("xxxxxxxxxxx", "xxxxxxxxxxx", "xxxxxxxxxxxxxxxxx") or die(mysql_error());
	mysql_select_db("xxxxxx") or die(mysql_error());
	$_data = mysql_query("SELECT username FROM user;") or die(mysql_error());
	print "<table>\n";
	while($_infoList = mysql_fetch_array($_data)) {
		$_userName = $_infoList['username'];
		if ($_width == 1) {
			print "<tr>\n<td>";
			print $_userName;
			print "</td>\n";
			$_width++;
			}
		 elseif ($_width == 2) {
			print "<td>";
			print $_userName;
			print "</td>\n";
			$_width++;
			}
		 elseif ($_width == 3) {
			print "<td>";
			print $_userName;
			print "</td>\n";
			$_width++;
			}
		elseif ($_width == 4) {
			print "<td>";
			print $_userName;
			print "</td>\n</tr>\n";
			$_width = 1;
		}
	}
	print "</tr>\n</table>\n</td>\n</tr>\n</table>\n</div>\n</body>\n</html>";


} elseif($_toWhere == 'edit') {
	print 'N/A';
}

} else {
//the session variable isn't registered, send them back to the login page
header( "Location: http://xxx.xxx.xxx.xxx/something" );
}


?>[/PHP]

---

