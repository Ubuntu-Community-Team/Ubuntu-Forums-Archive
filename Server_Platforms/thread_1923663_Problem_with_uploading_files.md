---
title: "Problem with uploading files"
date: 2012-02-11
forum: Server Platforms
---

### Post by mandza on 2012-02-11
Hi,
i have problem with uploading files and i dont know where the problem is, becouse of that i dont know what to search.

this is my code.
--------------------------------------
<html>
<head>
<meta http-equiv=\"content-type\" content=\"text/html; charset=utf-8\" /> 
<link media=\"all\" href=\"dizayn.css\" type=\"text/css\" rel=\"stylesheet\" /> 
<title>Pemax - Dosya Yükleme</title>
</head>
<body>
<form action=\"teknikservis_dosyaekle.php\" enctype=\"multipart/form-data\" method=\"post\">
<input type=\"hidden\" name=\"cihaz\" value=\"".$cihaz."\" />
<input type=\"hidden\" name=\"musteri\" value=\"".$musteri."\" />
<input type=\"file\" name=\"file\" /><br />
<input type=\"submit\" name=\"submit\" value=\"Dosya Ekle\" />
</form>
</body>
</html>
---------------------------------------------


---------------------------------------------

$cihaz=$_POST[cihaz];
$musteri=$_POST[musteri];
$dosyaismi=explode(".", $_FILES['file']['name']);
$boyut=$_FILES['file']['size'];
$uzanti=end($dosyaismi);

echo "$boyut - $uzanti - $cihaz - $musteri -";

/* i put echo just to see if there is information sended, but there is no any output.
i dont know is this problem with server or what.
this was working before.*/

//Eger cihaz bos degilse ve dosyan&#305;n uzant&#305;s&#305; rar ise dosya yüklemeye ba&#351;la
if(($uzanti=="rar" OR $uzanti=="zip") AND $cihaz!="" AND $musteri!="") {
$sondos=mysql_query("SELECT * FROM teknikservis_dosya WHERE 1 ORDER BY id DESC");
$sondosl=mysql_fetch_array($sondos);
$isim=($sondosl[id]+1);
$isims="drvr".$isim.".".$uzanti;
$time=time();
      move_uploaded_file($_FILES["file"]["tmp_name"], "dosya/drvr" . $isim . ".$uzanti");
$vtekle=mysql_query("INSERT INTO teknikservis_dosya(dosya, musteri, cihaz, tarih, boyut, uzanti) VALUES('$isims', '$musteri', '$cihaz', '$time', '$boyut', '$uzanti')");
      echo "<center>Dosya kaydedildi.<br />
<a href=\"javascript:void(0)\" onClick=\"javascript:self.close()\"><b>Pencereyi Kapat</b></a></center>";
} else {
echo "Dosya yuklerken hatta meydana geldi.";
}

-----------------------------------

---

### Post by SeijiSensei on 2012-02-12
You escaped all the quotes in the upload form.  Is this  being sent to the browser by an echo command from PHP, or is that the actual HTML that the browser receives?  What does View Source in the browser show?  If the browser is getting escaped quotes, I'm not sure how that will be handled.

You need to escape quotes if you're using echo and don't want the PHP interpreter to treat a quote as the end of the echoed string.  So, for instance,

```
echo "This string has an embedded \" in it."
```

is correct if rendered by PHP.  However the HTML the browser sees won't have the backslash.

---

