---
title: "Webmin &amp; Webserver"
date: 2005-09-27
forum: Server Platforms
---

### Post by Moonshine on 2005-09-27
I'm shortly going to try to install Apache, mySQL and php for a testing/non critical/occassionally showing friends images etc. on Ubuntu.

The guide on ubuntuguide.org looks simple enough for the installation of Apache, mySQL and php, but as I have a slow computer to do this on (400Mhz, 128mb ram) I need to make sure that I can a)
- Disable it running at start up &
- Uninstall it totally
Are there any security issues I need to be aware of with these...

And also;
I am going to follow [this]("http://ubuntuforums.org/showthread.php?t=7507") thread for information on Webmin. I'll change the default port, use a secure username and password and so forth. 
-Any other security issues with this I should be made aware of?
-Can I easily uninstall it?
- Start/stop it running at startup?
- Is there a good place where you can get themes to replace the somewhat ugly default one?

Thanks a lot.
**New question in 3rd post**

---

### Post by herrpoon on 2005-09-27
[QUOTE=Moonshine]I'm shortly going to try to install Apache, mySQL and php for a testing/non critical/occassionally showing friends images etc. on Ubuntu.

The guide on ubuntuguide.org looks simple enough for the installation of Apache, mySQL and php, but as I have a slow computer to do this on (400Mhz, 128mb ram) I need to make sure that I can a)
- Disable it running at start up &
- Uninstall it totally
Are there any security issues I need to be aware of with these...[/QUOTE]

I'm pretty sure that PC will run apache etc. fine, I've got a similar spec PC and I haven't had any problems.  Regrding the disabling/starting up, that's easy enough, just a command or two are needed.  Getting rid of apache and all the other stuff is a bit more complicated then just selecting remove program x as it is in windows but the following post explains all:

[http://ubuntuforums.org/showthread.php?t=66810](http://ubuntuforums.org/showthread.php?t=66810)

I'm not too sure about the second part as I haven't had much experience with webmin ;)

---

### Post by Moonshine on 2005-09-27
[QUOTE=herrpoon]I'm pretty sure that PC will run apache etc. fine, I've got a similar spec PC and I haven't had any problems.  Regrding the disabling/starting up, that's easy enough, just a command or two are needed.  Getting rid of apache and all the other stuff is a bit more complicated then just selecting remove program x as it is in windows but the following post explains all:

[http://ubuntuforums.org/showthread.php?t=66810](http://ubuntuforums.org/showthread.php?t=66810)

I'm not too sure about the second part as I haven't had much experience with webmin ;)[/QUOTE]

Ok thankyou for that information. Can anyone address the Webmin questions? Thanks.:)

[B]New question...
Edit:[/B] I installed Apache2, mySQL, php and webmin - All went fine. But now my port forwarding doesn't seem to be working. I have a Dlink 624 router and I have forwarded port 80 to the internal IP address (the 192.168 IP). If I go to the IP on other computers it works, but if I go to localhost then it doesn't. I'm not quite sure what I've done wrong. Do I have to change a configuration option with apache?

Thanks.

---

### Post by Glut on 2005-09-29
[QUOTE=Moonshine]
-Any other security issues with this I should be made aware of?[/QUOTE]
No, just do as you would for any secure web server.
> 
-Can I easily uninstall it?
Yes, in the same way that you'd remove any package. There is a gottcha, though: webmin stores many of its configs in it's own directory in etc. so if you do uninstall it, you may need to check that the config files are transferred to the preferred application location.
> 
- Start/stop it running at startup?
Yes, when you install it, it's setup to run on startup normally. To remove it, it's easy, but you should read the README in /etc/init.d because it's something that you don't want to screw up. The readme basically tells you where the real documentation is. I can't remember.
> 
- Is there a good place where you can get themes to replace the somewhat ugly default one?

No idea.

---

