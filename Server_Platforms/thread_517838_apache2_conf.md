---
title: "apache2 conf"
date: 2007-08-05
forum: Server Platforms
---

### Post by spur on 2007-08-05
I wish to be able to use my zip as my base dir for my files. I have altered 
/etc/apache2/sites-available default  so that the line for ScriptAlias reads 

ScriptAlias /cgi-bin/ /media/zip/
	<Directory "/media/zip/">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

There must be something wrong here as it does not work when I try to run the file hello-world.pl
I have added the handler and the php5 stuff (all of it) end enabled it. I can get the php files to work if I keep the original settings '/var/www/' , so php and apache are set up ok. I do want to use my zip as the dir though.

---

### Post by Warren Watts on 2007-08-05
I had similar difficulties when I first set up my apache2 server, but I remedied the problem by defining my VirtualHosts directly in apache2.conf instead of in the sites-available file.  Then I simply "remarked"  (with the # symbol) the include sites-available line in apache2.conf

---

### Post by spur on 2007-08-05
I don't know how to do that. I looked at it and am not sure what to put where. Could you show me how you did it? I know what is to be done its the how I need.

---

### Post by Warren Watts on 2007-08-05
first: make a backup copy of your apache2.conf file:
```
sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak
```
then copy and paste the contents of your default file in sites-available onto the bottom of apache.conf.

put a # symbol in front of the line at the bottom of apache2.conf that says include /etc/apache2/sites-available/default

save your changes

then stop and restart apache. (I usually use System | Administration  | Services to accomplish this)

---

### Post by spur on 2007-08-05
Thanks for that I did it but it seems to not be working when I put 'http://localhost/hello-world.pl' in the adress bar I get  a 'forbidden' message.
When I put in the complete address 'http://localhost/media/zip/ etc" I get a "not found" error.
I am wondering about my wording of the ScriptAlias and Directory line. The first bit I understand to be the 'real' place and the second the actual one.
Also if the final '/' should be there.

---

### Post by Warren Watts on 2007-08-05
You have to change the file permissions on your perl script to allow it to be run thru your server.

use chmod to accomplish this.
```

sudo chmod 755 /thepath/toyour/perlscript.pl 
```

---

### Post by Warren Watts on 2007-08-05
> **spur said:**
> When I put in the complete address 'http://localhost/media/zip/ etc" I get a "not found" error.

You can't call a location on your filesystem tree like that.  Whatever you set the 
DocumentRoot to in your apache2.conf file is going to be [http://localhost](http://localhost)

so unless you have a directory called media underneath the directory you defined as DocumentRoot, it isn't going to find it.

Looking a little deeper at your original post, you are defining an alias for your cgi-bin directory... That would make the path to your file [http://localhost/cgi-bin/yourperlscript.pl](http://localhost/cgi-bin/yourperlscript.pl)

For example: my cgi-bin folder is aliased to a folder in my /home directory.  so the path to a perl script I have written is:
```
http://kingbeetle.servehttp.com/cgi-bin/MAC_address_lookup.pl
```

---

### Post by spur on 2007-08-05
Thanks for that so I take the /media/zip/ as the root of the file and don't include it. My file is already 755.

---

### Post by Warren Watts on 2007-08-05
I edited my reply (maybe since you read it)  to clarify a few issues so you may want to refresh the thread and read my reply again...

---

### Post by spur on 2007-08-05
Thanks for your troubles. I have the adress thing sorted but I now get the download dialogue. I thought that as I had put the handler in I would not get that. I will copy th config file and post it as an attachment as a text file so you can lookat it if you will.

---

### Post by spur on 2007-08-05
This is the file I've packed it as it was too big to upload.

---

### Post by Warren Watts on 2007-08-05
The only difference I see between your apache2.conf and mine is the extra "/" at the end of **<Directory "/media/zip/">**, but that shouldn't make any difference.  In fact, I edited my config file and added a "/" and it still worked...
what are the file permissions set to for the folder the perl script is in?

is it the root folder of the zip drive?

you want to chroot the folder to the same file permissions as the perl script.

---

### Post by Warren Watts on 2007-08-05
One other thing I noticed: you have the 

AddHandler cgi-script .cgi directive un-remarked, with .pl added.

In my config file the directive  is remarked out (has a # symbol in front of it)

you might try remarking out this directive.

And of course, remember to stop and restart the server whenever you make changes to apache2.conf

---

### Post by spur on 2007-08-05
No change if I put a remark (#) before the addhandler line. The book I was using and the examples say that the line needs to be there for it to be able to handle the perl scripts. In what other way can this be accomplished or is it somewhere else by default?

---

### Post by Warren Watts on 2007-08-05
Sorry I didn't respond sooner.. It was 4:30 in the morning last night and I had to get some sleep...

At this point I am somewhat baffled. Your configuration file and mine don't really differ in any other significant ways, yet I don't have any problems with apache executing Perl scripts, and you do.

Any one else out there have any suggestions?

---

### Post by spur on 2007-08-05
Thanks for your help so far Warren.I didn't look at your local. I'm in Australia (=+10 GMT) so our times are a lot different. I appreciate your patience. I'll fiddle with the permissions as my zip is a fat32 and that may be at the heart of it. The files were all produced on ubuntu though?

---

### Post by spur on 2007-08-09
I have got things working as long as I use a folder on my hard drive as my cgi-bin directory. I think that using a folder on my zip caused the she-bang line to direct to the root of the zip for perl. I haven't been able to work how to get it to direct to the hard drive root ie '/usr/bin/perl.' instead of '/media/zip/usr/bin/perl/'. It seems a '/usr/bin/perl' on the she-bang line of a file in the zip drive is interpreted as beginning with 'media/zip' (my zip drive mount point).

---

