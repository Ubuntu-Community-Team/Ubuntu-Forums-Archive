---
title: "LAMP Server - Apache Only See 0Text"
date: 2012-02-27
forum: Server Platforms
---

### Post by techblvd on 2012-02-27
Total newb here.  I just installed a LAMP server (Ubuntu 11.10).  I have a couple of small sites that I have been running on a Windows 2003 server with IIS.  They are basic static pages.  I copied the site from the IIS server to the new LAMP server.  I believe the virtualhost is setup correctly since I can get to the page from both internal and external machines.  I can see only white backgrounds and only the text from the pages.  I don't see any of the backgrounds, pictures, links, etc...

I am going to need this explained to me like a 2 year old :(

The sites were all created in IWeb.

Thanks!!

---

### Post by spynappels on 2012-02-28
Was there an assets folder which stored all graphics, css files etc. which did not copy correctly? Are the permissions set correctly for this folder if it exists?

Are the relative paths to any graphics etc. correct?

---

### Post by SeijiSensei on 2012-02-28
You're probably missing the CSS stylesheets and associated graphics.  

If you use Firefox, I recommend opening a page, the right-clicking on it and choosing View Page Source.  Up at the top in the <head></head> section there may be a <link rel="stylesheet"> tag that points to a file with the extension .css.  If you click that link, you should see the stylesheet.  (You can see an example by viewing the source of this page.)  If that link goes nowhere, as I suspect it will, you didn't copy over everything associated with the site.

Did you copy the entire directory, or just a few .html files?

---

### Post by techblvd on 2012-02-28
Hmm, ok....I checked to see that the files were all there and they are.  However, when I click the link to the .css page in the source, I see:

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>403 Forbidden</title>
</head><body>
<h1>Forbidden</h1>
<p>You don't have permission to access /Home_files/Home.css
on this server.</p>
<hr>
<address>Apache/2.2.20 (Ubuntu) Server at localhost Port 2113</address>
</body></html>

Looks like a permissions issue.

I will give you a little background.  I originally installed this server and chose to encrypt home.  I put the files for my site in a directory in my home folder called public_html.  I was never able to get it to come up.  I kept getting 403 errors.  So, I assumed it was because of the encryption and permissions.

I then re-installed the server, choosing to NOT encrypt home (I am sure i could have done that without re-installing but I wanted the practice).  I copied the folder containing the site to the newly created public_html folder and created a virtualhost file for it and set it active.  I am running it on port 2113 so I had to tell it to listen on that port.  That all seems to have gone fine.  I did not chmod the folder containing the site or any of its files.  Could that be the issue?  I understand I can chmod 777 to open it up.  I also understand that is not the proper way to leave it.  

Should I chmod 777 or is there a best practice for permissions to the site folder?  I have read the the apache service needs particular rights.  I am not sure exactly how to set this properly.

The paths to the graphics are set similarly to this:

<div style="height: 8px; width: 666px;  height: 8px; left: 17px; position: absolute; top: 3px; width: 666px; z-index: 1; " class="tinyText style_SkipStroke_2">
              <img src="Home_files/MainEvent_horizontal_line1.png" alt="" style="border: none; height: 8px; width: 666px; " />
            </div>

There is also pointers to a scripts folder that contains .js files.  I assume I don't need to do anything special for apache to handle those.


Thanks again :)

---

### Post by CharlesA on 2012-02-28
I'd go with chmod 664 not 777. Nothing that apache serves needs execute permissions.

---

### Post by techblvd on 2012-02-28
Thanks,

664 didn't work.  I had no access at all.  777 works.  Is that too open?

---

### Post by techblvd on 2012-02-28
Thanks,

With 664 i lost access completely.  777 seems to work fine.  Is that too open?

---

### Post by CharlesA on 2012-02-28
If the files are stored in folders, the folders need execute permission.

The command you can run should look something like this.

```
sudo chmod -R og+rwX a+rX /path/to/base/folder/
```

---

### Post by SeijiSensei on 2012-02-28
By default, /home/user has 700 permissions, so that only the user has access to any of the files in any of the directories below /home/user.

When you put something that needs to be publicly visible like a website into a directory below /home/user, the absence of the execute bits on that directory makes it impossible for any other users to list that directory.  In particular, the "www-data" user under which Apache runs cannot access anything below /home/user.

The solution to this is to give 711 permissions to /home/user; this grants group and other users the ability to see directories below that one, though not to read or write any files located there.  You'll still need to make /home/user/public_html 755, granting everyone the ability to read and list the files in that directory.  The files themselves should have 644 permissions.

```

[user@host ~]$ cd /home
[user@host /home]$ sudo chmod 711 user
[user@host /home]$ cd ~
[user@host ~]$ chmod 755 public_html
[user@host ~]$ chmod ugo+r public_html/*

```

If you have additional directories below public_html, they must have 755 permissions as well.

---

### Post by techblvd on 2012-02-29
Thank you to all of you for the great information.  Everything is working perfectly :)

---

