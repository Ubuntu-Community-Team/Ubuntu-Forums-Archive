---
title: "Webmin alternatives"
date: 2013-01-10
forum: Server Platforms
---

### Post by fernandoch on 2013-01-10
Hello,

I installed webmin but it is showing me a lot of modules as unused, although the servers are working properly like for example mysql server or the apache server. I tried to fix it, but I could not. Are there any good alternatives for webmin? What about Zentyal?

Thank you.

---

### Post by LinuxBill on 2013-01-10
Never used Zentyal, but for for mySQL you could use myPHPadmin? Think it only for mySQL servers though. 
 
Bill

---

### Post by fernandoch on 2013-01-10
I know, I know, but I don't like to have unused modules when the server is working properly like apache webserver too...

I believe webmin is better for redhat based systems...

---

### Post by Cheesemill on 2013-01-10
I like Zentyal, I use it on a few of my clients servers.

Try it out in a VM and see what you think.

---

### Post by fernandoch on 2013-01-10
What about webmin? Better to stay away from it?

---

### Post by LinuxBill on 2013-01-10
I think webmin great if you want a GUI. I tend to stick with the terminal for most. But SQL i like a GUI, im no DBadmin ha!

---

### Post by Groodles on 2013-01-10
Webmin is a crutch.

Learn to embrace SSH, the cmdline and .conf files.

---

### Post by ericje627 on 2013-01-11
> **fernandoch said:**
> I know, I know, but I don't like to have unused modules when the server is working properly like apache webserver too...

I believe webmin is better for redhat based systems...

When webmin is not detecting the servers automatically, there is an option to force a recheck on webmin modules. This can be found under Webmin->Webmin configuration->Refresh modules.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229882&d=1357887336[/IMG]

---

### Post by fernandoch on 2013-01-11
I already did a refresh and it did not work.

Today I connected, and the modules I wanted like apache server and mysql were not in the un-used modules, they were enabled...

Very strange, anyways thank you to all.

---

### Post by SeijiSensei on 2013-01-11
> **fernandoch said:**
> I believe webmin is better for redhat based systems...

Everything I see about Webmin with Debian/Ubuntu installations suggests it has problems.  Why not switch your server to CentOS 6?  Webmin works fine with that.

---

### Post by mysteriousdarren on 2013-01-11
+1 for myPHPadmin, its my second choice. Webmin has always been first choice.

---

### Post by kevinthecomputerguy on 2013-01-12
I too have heard CentOS and Webmin is a match made in heaven.

Things to remember are

Webmin is free
Ubuntu is bleeding edge

Free and bleeding edge dont usually mix, but i think the webmin guy does an awesome job across the distros. Knowing its his own nights and weekends, i say hats off, great job.

I primarily use Debian, and haven't had any issues on stable versions.

I have had issues with Ubuntu, but the cause was because Ubuntu made a drastic and or unconventional change, but thats why we love Ubuntu.

Webmin is a great product, by far my favorite, i love it on Debian, and i heard the developer users CentOS.

You shouldn't run a server without knowing CLI and SSH, but Webmin is a great tool in your tool-belt, and can save you alot of time. I like to save my hard to remember CLI commands into custom Webmin buttons.

---

