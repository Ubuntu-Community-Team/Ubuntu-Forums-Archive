---
title: "Compress folder using zip command with PHP"
date: 2012-09-28
forum: Server Platforms
---

### Post by alfirdaous on 2012-09-28
Hello everybody,

While using zip command line with PHP to add a folder into an archive file:

General command:

```

zip archive.zip file.mp3

```


PHP code:
[PHP]
 <?php
$path2mp3 = '../Downloads/Medias/MP3/001.mp3';
$site = 'site.com';
$compressFolder = $site.'.zip';
$cmd = "zip -r $compressFolder $path2mp3";
                        
$compressMP3 = exec($cmd ." 2>&1" );
echo $compressMP3;
                        
if($compressMP3)
{
echo 'Done';
}
else
{
echo 'Not Done';
}

?>

  

[/PHP]

Output:

```

updating: ../Downloads/Medias/MP3/001.mp3 (deflated 6%)
```

I cannot find the file, and I don't know whether it is created or not.

In command line:

```

$ zip archive.zip 001.mp3 
  adding: 001.mp3 (deflated 6%)
$ ls
archive.zip


```

Thanks in advance

---

### Post by SeijiSensei on 2012-09-28
Are you running this script via Apache or at the command-line?

If the former, you may have file permission issues since any files created will be owned by user www-data and must be placed in a directory to which www-data has write permissions.

If you are running this at the command line, why are you using PHP?  Just write a shell script.

---

### Post by alfirdaous on 2012-09-29
it is a PHP script, not a command line:

[PHP]
$cmd = 'cd ../MP3 && /usr/bin/zip --password pass --encrypt -r '.$path2root.$compressedFile.'  *.mp3';
[/PHP]

using password will protect the zip file, how about the option --encrypt, what is the use for?

---

