---
title: "Apache2 boot script"
date: 2005-05-10
forum: Server Platforms
---

### Post by Abnormal1 on 2005-05-10
newbie warning!

Hi,
Ive been having problems setting up apache to use php etc and I recently discovered that apache2 was not running and instead apache was.

I have removed apache via apt-get just in case it was causing a problem with apache2 but that did not fix it.

Anyway I discovered that if i run apache2ctl my web server starts working just fine. However if i run /etc/init.d/apache2 the only command that seems to work is stop.
If i use start etc I don't get any messages but if i use the stop command i get Stopping web server (Apache2)...

I assume that for some reason the apache script is not running correctly however I don't no why.

Any help would be greatly appreciated

Thanks
Abnroaml1

---

### Post by qstone on 2005-05-12
just one (stupid?) question : do you run /etc/init.d/apache2 as root (or via sudo) ?

---

### Post by spartas on 2005-05-12
[QUOTE=qstone]just one (stupid?) question : do you run /etc/init.d/apache2 as root (or via sudo) ?[/QUOTE]


Try the following command if apache is not running:

> 
sudo ./etc/init.d/apache2 start


or this if it is running


> 
sudo ./etc/init.d/apache2 restart


---

### Post by Abnormal1 on 2005-05-13
Currently I log in as root as don't have patience for sudo while setting up server. Anyway I managed to bodge it so that apache2 starts at boot by putting */usr/sbin/apache2ctl start*  at the beginning of the init script

beginning of apache2 init script:> #!/bin/sh -e
#
# apache2        This init.d script is used to start apache2.
#            It basically just calls apache2ctl.

/usr/sbin/apache2ctl start

@spartas if I do that with a . (DOT) in it i get *sudo: ./etc/init.d/apache2: command not found*

Without the . (DOT) i just get nothing as I explained earlier. I only get a response from the script with stop.

Abnormal1

---

### Post by zaphod288 on 2005-06-14
Ok this had me stumped as well.  

You need to edit /etc/default/apache2 file

Change NO_START=1  to  0

This by the looks of it is default security on a new install so people dont just fire up an apache2 server thinking its agreat idea by apt-get.

I found there was nothing wrong with /etc/init.d/apache2 script, other than it didnt tell you it couldn't start apache2 because of this setting in its default file.

I hope this helped as I had spent the last day also trying to work out why /etc/init.d/apache2 was not starting my webserver.

---

### Post by LordHunter317 on 2005-06-14
No, it's to prevent Apache 2 from stomping on Apache 1.3's toes. 

And only people who don't understand how to use sudo say, "I use root because I don't have the patience for sudo during setup" or anything of that ilk.

---

### Post by zaphod288 on 2005-06-15
[QUOTE=LordHunter317]No, it's to prevent Apache 2 from stomping on Apache 1.3's toes.[/QUOTE]

That is a better reason, as I was implying above, I was only guessing to why it was switched off out of the box.  I had to post above as I was having the same problem and refused to believe I had to butcher the /etc/init.d/apache2 script to make it start apache2. After searching and not finding the answer any where in these forums, I thought it might be useful to post a solution rather than flaming peoples opinions.

---

### Post by LordHunter317 on 2005-06-15
[QUOTE=zaphod288]  I had to post above as I was having the same problem and refused to believe I had to butcher the /etc/init.d/apache2 script to make it start apache2.[/quote]There are other scripts where you would have to, no worries.

>  After searching and not finding the answer any where in these forums, I thought it might be useful to post a solution rather than flaming peoples opinions.Eh?

---

### Post by Abnormal1 on 2005-06-16
@zaphod288
Thanks for that. Changing NO_START fixed my problem as apache2 now start correctly at boot. I was not happy with butchering the start script either but was getting Desperate.

I wish i had never mentioned not using sudo now as there appears to be a lot of Prejudice against people not using it here.

Also the reason I have not been using it was that I was getting very frustrated trying to get Linux to do what I wanted and having to type in a password all the time was not helping. I obviously don't understand sudo and do intend to research it when i get time.

Abnormal1

---

### Post by LordHunter317 on 2005-06-16
[QUOTE=Abnormal1]I wish i had never mentioned not using sudo now as there appears to be a lot of Prejudice against people not using it here.[/quote]If you choose not to use it, that's fine.  However, your stated reason for not using it is nonsensical and only demonstrates you didn't take any time to understand how to use the tool.  Which isn't a good reason to not use something.   Especially when reading the manpage would show you can run 'sudo -s' or 'sudo /bin/sh' to get a root shell anyway.

---

### Post by Abnormal1 on 2005-06-16
> LordHunter317
Especially when reading the manpage would show you can run 'sudo -s' or 'sudo /bin/sh' to get a root shell anyway.

That would make it a lot eaiser to work with. I will remember that and I do intend to read the documents on sudo.

Something else I was wondering was does everyone have to change NO_START to get apache2 to work and i missed it in the docs or is it rare. If it is rare then does anyone no why we had to do this.

Abnormal1

---

### Post by LordHunter317 on 2005-06-16
I believe it only gets set to true if apache one is installed, to prevent existing installs from conflicting, like I said.

If you don't have Apache 1.3 installed when you install Apache 2, then the apache2 package assumes it is the default and runs by default, because it can't conflict with anything.

---

