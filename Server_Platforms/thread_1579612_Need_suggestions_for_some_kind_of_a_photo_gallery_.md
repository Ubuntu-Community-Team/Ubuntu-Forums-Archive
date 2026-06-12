---
title: "Need suggestions for some kind of a photo gallery software"
date: 2010-09-22
forum: Server Platforms
---

### Post by harisund on 2010-09-22
Hello guys !!

So I have an internet accessible desktop. To that, I have attached a terabyte hard disk. In my fstab I have made the necessary modifications so that the hard disk is mounted in a directory within my ~ HOME directory, and mounted with uid,gid of my user. In that, there's a "Photographs" directory, and plenty of sub directories, each with potentially more subdirectories with photographs. 

What I want to be able to do is easily display the photographs on the web. I have registered dynamic DNS with dyndns.com and have a hostname (harisund.homelinux.com !) 

A. I want the gallery software to automatically display the folders I have in that ~/TerabyteMountPoint/Photographs folder in a photo gallery format. 
B. For the purpose of the webpage, the resolution of the images should be small. 
C. Users should be given the option of downloading the pictures/directories they want, and with the full resolution if they so desire. 

Any suggestions? I have a Ubuntu server installation on this desktop, with LAMP enabled !

---

### Post by SeijiSensei on 2010-09-22
Here's a PHP script I wrote to display a bunch of image files in a tabular format.  You're welcome to it.

```

        <html>
        <head><title>My Photographs</title></head>

        <body>

	<h3>My Photographs</h3>
    
        <p>Click on an image to make it full-size.</p>    
        <p>Right-click an image and choose "Save" to download it.</p>	

<?php

# set these as desired
$imgdir="/path/to/your/photographs/directory";
$max_width=150;   # maximum displayed width of thumbnails
$per_row=4;       # number of images per row

# here be monsters, cap'n
$files=explode("\n",`ls $imgdir | egrep 'gif|png|jpg|jpeg'`);
$rows=ceil(count($files)/$per_row);
#echo "<h4>rows=$rows</h4>";
$avcounter=0;
?>
	<h4>There are <?=count($files)?> images available.</h4>
	
	<table>
	
<?php
for ($r=0; $r<$rows; $r++) {
	
	$sizerow="";
	echo "<tr>";
	
	for ($c=0; $c<$per_row; $c++) {
	    
	    if (!empty($files[$avcounter])) {
		$fn=$imgdir.$files[$avcounter];
		$imgdata=getimagesize($fn);
		$width=$imgdata[0];
		$height=$imgdata[1];
		#echo "<h4>imgdata for '$fn' has ".count($imgdata)." elements</h4>";
		
		$sizerow.="<td style=\"padding-left: 12px; padding-right: 12px\">".
		  $files[$avcounter]."<br/>($width x $height) ";
		
		$fs=filesize($imgdir.$files[$avcounter]);
		if ($fs < 2048) {
		    $sizerow.=number_format($fs)."B";
		} else {
		    $sizerow.=number_format($fs/1024)."K";
		}
		
		if ($width>$max_width) {		    
		    $scale=$max_width/$imgdata[0];
		    $width=floor($width*$scale);
		    $height=floor($height*$scale);
		}		 
		$imgsize="width=$width height=$height";
		
		echo "<td style=\"padding:12px\">";
		echo "<a href=\"/images/".$files[$avcounter]."\">";
		echo "<img $imgsize src=\"/images/".$files[$avcounter]."\"></a></td>";
	    
	    }
	    
	    $avcounter++;
	    if ($avcounter>count($files)) {
		echo "</tr>\n";
		break;
	    } 
	    
	}
    
    echo "</tr>\n";
    echo "<tr>$sizerow</tr>\n";
}
?>
	</table>

        </body>

        </html>

```

Call the file index.php and place it in the root of the website tree.  Make sure any other index files like index.html are renamed to force the server to use the PHP script by defalt.

The results look like [this]("http://www.takinganimeseriously.com/images/avatars/").

---

### Post by Dragonbite on 2010-09-22
Run [[COLOR="Blue"]_Gallery_[/COLOR]]("http://gallery.menalto.com/")?  There is also a module for it in Drupal if you prefer CMSs.

---

### Post by philinux on 2010-09-22
Moved to Server Platforms.

---

