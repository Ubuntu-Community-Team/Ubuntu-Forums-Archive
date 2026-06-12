---
title: "apache / php file permissions"
date: 2010-09-28
forum: Server Platforms
---

### Post by losthawken on 2010-09-28
Hi all,

I'm learning PHP and I'm working on a simple page to upload a file.  I'm running Ubuntu 10.0.4 and with Apache2 and PHP5 installed to develop and test.

I've written the basic script and it works fine.  The problem is that the uploaded file has permissions granted only to root.   I've tried chmod from within the php script, but it doesn't seem to work, I'm guessing that it is a problem coming from apache?

The problem is true for any file that the scripts I'm using create.

Thanks in advance,

~Justin

---

### Post by windependence on 2010-09-28
How are you uploading your files? The problem is coming from this program.
 
-Tim

---

### Post by losthawken on 2010-09-28
I'm using firefox to run the test pages.  Below is the script:

> Index.php
<form enctype="multipart/form-data" action="upload.php" method="POST"> 
    Please choose a file: 
    <input name="uploaded" type="file" /><br /> 
    <input type="submit" value="Upload" /> 
</form> This page sends the files to the next page:
> upload.php
echo "uploading<br />";
$target = "upload/"; 
$target = $target . basename($_FILES['uploaded']['name']) ; 
$ok = 1; 
if(move_uploaded_file($_FILES['uploaded']['tmp_name'], "upload/ListC.csv")) {
 
    echo "The file ". basename( $_FILES['uploaded']['name']). " has been uploaded <br/>"; 
} 
else { 
    echo "Sorry, there was a problem uploading your file. <br />"; 
}This is puts the files into the 'upload' folder within the same directory that upload.php resides in.  Again, the files get where they need to go, its just that they are restricted to root access only.  Adding chmod 0777 to the script doesn't seem to help.

---

### Post by windependence on 2010-09-28
Well, you wouldn't want them world writable anyway. You need to chown not chmod your files. Chown the files to the apache user (usually www or www-data).
 
-Tim

---

### Post by losthawken on 2010-09-28
OK, I tried that here:

> $user = $www-data;
if(move_uploaded_file($_FILES['uploaded']['tmp_name'], "upload/ListC.csv")) {
    $chowner = chown ("upload/ListC.csv", $user);
 if  ($chowner) {
     echo "chowned<br />";
    }
    else {
        echo "not chowned<br />";
    }
    echo "The file ". basename( $_FILES['uploaded']['name']). " has been uploaded <br/>"; 
} 
else { 
    echo "Sorry, there was a problem uploading your file. <br />"; 
}I get back a 'not chowned'... :confused:  I'm really missing something here.

---

### Post by SeijiSensei on 2010-09-28
First off, I'd be surprised if the files when uploaded are owned by root.  They should all be owned by www-data since that's the user that apache runs as.  You'd have had to modify Apache (in a very insecure manner) to have any files it creates be owned by root.

In a script I've written to process uploaded files, I used something like this:
```

$target_filename="/path/to/the/target_directory/target_filename";
$move=move_uploaded_file($_FILES["thisfile"]["tmp_name"],$target_filename);                     

if ($move) {
    # do stuff if the move worked properly
    @chmod($target_filename,0664);      

} else {
    complain();

}

```

Using complete paths is almost always a good idea in situations like this.

---

### Post by losthawken on 2010-09-29
:/ I don't think that I modified Apache, but I'm still a newb.  Just for the sake of saying it , I am a newb, but I only tried to chmod to 0777 as a disparate attempt to get SOMETHING to work I agree that it would be a bad choice of mode fir files actually posted to a server.

I've tested the uid, and gid, it seems to be root, heres an image of the file properties:

[IMG]http://ubuntuforums.org/picture.php?albumid=2037&pictureid=6787[/IMG]

Could it be an odd setting in ubuntu?

I have to use sudo to chmod and chown the file from the command line.  :confused:

---

### Post by SeijiSensei on 2010-09-29
sudo chown www-data.www-data /path/to/ListC.csv
sudo chmod 0644 /path/to/ListC.csv

Is this the very first instance of the file ever written?  Did you put it there only via your PHP script?  I'm guessing there was an original copy already present that had root ownership so Apache can't modify the file.

Let's try a simple test.  Add the line 

exec("touch /tmp/test");

to the top of upload.php.  This will create a file called test in the /tmp directory.  See what ownership and permissions it has.

---

### Post by losthawken on 2010-09-29
> **SeijiSensei said:**
> sudo chown www-data.www-data /path/to/ListC.csv
sudo chmod 0644 /path/to/ListC.csv

Is this the very first instance of the file ever written?  Did you put it there only via your PHP script?  I'm guessing there was an original copy already present that had root ownership so Apache can't modify the file.

Let's try a simple test.  Add the line 

exec("touch /tmp/test");

to the top of upload.php.  This will create a file called test in the /tmp directory.  See what ownership and permissions it has.

The file was 'uploaded' from another location on the computer.  I'm not sure if I can say its the 'first' instance of the file, b/c I've deleted it and had the PHP script upload it or write over it dozens of times trying to get it to work.  

exec("touch /tmp/test")

does nothing, no file was created.  I created the /tmp directory and still no file.  I tried the touch /tmp/test command from the command line, and it reported 'permission denied'.

---

### Post by SeijiSensei on 2010-09-29
You *created* the /tmp directory?  Where?  /tmp is a basic part of every Linux filesystem tree and should have been created at installation.  Did you install the OS from scratch?  Which distro/version?  Something seems borked about your system.

---

### Post by losthawken on 2010-09-29
> **SeijiSensei said:**
> You *created* the /tmp directory?  Where?  /tmp is a basic part of every Linux filesystem tree and should have been created at installation.  Did you install the OS from scratch?  Which distro/version?  Something seems borked about your system.

Right, /tmp  IS in the linix filesystem.  

I redirected apache to load pages from /media/truecrypt1/web, where I keep my in-development pages, by modifying the virtualhost file under etc/apache2/sites-available.

I assumed that the php script would look within /media/truecrypt1/web for /tmp since that is where it is located.  All the other commands from the script have started within the /web directory...  

(I feel like this is going to end withme saying,  "I can't believe I am so dumb")

---

### Post by losthawken on 2010-09-29
OK so I looked in the REAL /tmp directory and the test file was there. :oops:

It is owned by www-data with permissions of 0655.  Oddly, I should be included in the www-data group but the file properties -> permissions tab doesn't give me the option to change anything.

---

### Post by SeijiSensei on 2010-09-29
> **losthawken said:**
> OK so I looked in the REAL /tmp directory and the test file was there. :oops:

It is owned by www-data with permissions of 0655.  Oddly, I should be included in the www-data group but the file properties -> permissions tab doesn't give me the option to change anything.

Edit /etc/group with "sudo nano /etc/group" or whatever editor you choose, then add your username to the end of the www-data line like this:

www-data:x:33:yourusername

Notice, though, that you'll still only have read/execute privileges on the files Apache writes if they have 0655 permissions.  You'd need to chmod them in your script to 0665; actually, I'd recommend 0664 to protect against the possibility of someone uploading a script and running it from the destination directory.  0660 is even better if you're security conscious.

So now go back to the directory where the csv file was stored, delete it with "sudo rm", then try uploading it again with your script.  Does it work now?

---

### Post by losthawken on 2010-09-29
> **SeijiSensei said:**
> Edit /etc/group with "sudo nano /etc/group" or whatever editor you choose, then add your username to the end of the www-data line like this:

www-data:x:33:yourusername

Notice, though, that you'll still only have read/execute privileges on the files Apache writes if they have 0655 permissions.  You'd need to chmod them in your script to 0665; actually, I'd recommend 0664 to protect against the possibility of someone uploading a script and running it from the destination directory.  0660 is even better if you're security conscious.

So now go back to the directory where the csv file was stored, delete it with "sudo rm", then try uploading it again with your script.  Does it work now?

/etc/group ->www-data was already set correctly, I checked.

sudo rm'ed ListC.csv

reloaded the index page, selected the file to upload, uploaded. checked file perms...

Fail.  still belongs to root...  

I'm going to try moving the file into a different location with a different filename and see what happens.  I'll let you know.

---

### Post by losthawken on 2010-09-29
OK, so I can get the script to make the file to the /tmp folder, and it does so with proper permissions.

BUT, if I use the script to make the file anywhere under /home it fails.

The same is true of any other mounted media directory

But if I make the file anywhere in /media/truecrypt1/ directory (the virtual encrypted media directory in which the script lives) it makes with the root owner permissions only.

I'm guessing that I'm trying to run the web page from a wierd directory that is confusing the system.  I'll try relocating the /web folder and reconfiguring apache.

---

### Post by SeijiSensei on 2010-09-29
By default user directories under /home have 0700 permissions so other users can't write anything to them.  Even if you make a directory below /home/username world-writable, you have to change the permissions on/home/username itself to at least 0711.

You can enable Apache to write to other directories by changing their groups to www-data with chgrp then assigning group-writable permissions to those directories and the file they contain if appropriate with chmod.

I don't use Truecrypt so I can't help with that.

---

### Post by windependence on 2010-09-30
I might add that keeping the default locations of your apache files will make your life much easier later down the road when you decide to upgrade your packages or your OS. All kind of weird things can happen if you insist on putting your files all over in non-standard locations.
 
-Tim

---

