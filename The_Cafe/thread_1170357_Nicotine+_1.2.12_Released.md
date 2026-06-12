---
title: "Nicotine+ 1.2.12 Released"
date: 2009-05-26
forum: The Cafe
---

### Post by OffHand on 2009-05-26
We have just released a new version of Nicotine+ with tons of bug fixes. We now have a brand spanking new OS X installer (drag 'n drop) too!

Download the tarball from [our website]("http://www.nicotine-plus.org/") or the [deb package]("http://packages.debian.org/sid/all/nicotine/download")  from the Debian website.

[CHANGELOG]("http://www.nicotine-plus.org/browser/trunk/nicotine%2B/doc/CHANGELOG")


You can also use the script that will install the latest nicotine release (into /opt) while keeping your install from the repository. Make the script executable ```
chmod +x versionbump_nicotine.sh
``` Run the script from your home folder.```
sudo sh versionbump_nicotine.sh
```

How to revert back to the version from the repositories
```

sudo rm /usr/bin/nicotine
sudo dpkg-divert --rename --remove /usr/bin/nicotine
sudo rm -r /opt/nicotine+-*

```

---

### Post by el-mar01 on 2009-05-26
Where is the .deb file ??

---

### Post by OffHand on 2009-05-26
There isn't any yet, but you can [easily run it from source]("http://ubuntuforums.org/showpost.php?p=1698178&postcount=146"). No need to install  :)

There will be one eventually.... any deb packagers around?

---

### Post by OffHand on 2009-05-27
bump

---

### Post by Greenwidth on 2009-05-28
Thanks!

---

### Post by binbash on 2009-05-28
Nice release but a debian package would make it better : )

---

### Post by pwnst*r on 2009-05-28
wow, i didn't know soulseek still existed.

---

### Post by OffHand on 2009-05-28
Soulseek is still going strong! We are working on a deb package. No ETA though. Hopefully 1.2.12 will be in the upcomming release (ubuntu 9.10).

---

### Post by fatality_uk on 2009-05-28
> **OffHand said:**
> There isn't any yet, but you can [easily run it from source]("http://ubuntuforums.org/showpost.php?p=1698178&postcount=146"). No need to install  :)

There will be one eventually.... any deb packagers around?

This might help.

[http://showmedo.com/videotutorials/video?name=linuxJensMakingDeb](http://showmedo.com/videotutorials/video?name=linuxJensMakingDeb)

---

### Post by monsterstack on 2009-05-28
Awesome stuff. A native Soulseek client was the first piece of software I searched for after doing away with Windows. Nicotine has just been awesome for me. Keep up the good work. :)

---

### Post by Eisenwinter on 2009-05-28
Thanks, I updated to it.

---

### Post by OffHand on 2009-05-28
> **fatality_uk said:**
> This might help.

[http://showmedo.com/videotutorials/video?name=linuxJensMakingDeb](http://showmedo.com/videotutorials/video?name=linuxJensMakingDeb)

Cheers. I'll see what I can do if I find the time ;)

---

### Post by el-mar01 on 2009-05-29
There is a program that allows you to create a .deb file .. it looks pretty easy to do [http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/](http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/)

---

### Post by Greenwidth on 2009-05-29
Is Nic+ 1.2.12 now allowed to use the distributed search tree?
I'm actually uploading to win clients for the first time!

---

### Post by Eisenwinter on 2009-05-29
> **Greenwidth said:**
> I'm actually uploading to win clients for the first time!
Me too! It's great.

I used to get banned by people because for some reason, the previous versions of N+ wouldn't let me upload files, to **anyone**!

There was also an issue with download speeds for me. Whenever a track would finish the downloading, the next track (from the same user) would always be downloaded at outragous speeds (1 KB/s and below!)


This version seems to have fixed those big problems. Thanks Nicotine+ team!

---

### Post by OffHand on 2009-05-29
> **Eisenwinter said:**
> Me too! It's great.

I used to get banned by people because for some reason, the previous versions of N+ wouldn't let me upload files, to **anyone**!

Now that's something that probably doesn't have anything to do with being in the distributed searches. The SoulSeek sys admins cut of 3rd party clients like N+ from partaking in distributed searches. They seem to have changed their policy  :)

---

### Post by OffHand on 2009-05-29
> **el-mar01 said:**
> There is a program that allows you to create a .deb file .. it looks pretty easy to do [http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/](http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/)
I'll take a look but it's almost weekend and it's going to be 24C (for people that don't use Celcius, 24C is freaking nice!). I think you gotta use it from source a little bit longer ;)

---

### Post by OffHand on 2009-05-29
I made a script that will install the latest nicotine release while keeping your install from the repository. Run the script with sudo from your home folder.

---

### Post by pt123 on 2009-05-29
I remember requesting for deb 6 months ago
[http://ubuntuforums.org/showpost.php?p=6341714&postcount=9](http://ubuntuforums.org/showpost.php?p=6341714&postcount=9)

atleast their has been a change in attitude

a shame many linux open source developers fail to see power of the .deb in attracting a large user base.

---

### Post by OffHand on 2009-05-29
> **pt123 said:**
> I remember requesting for deb 6 months ago
[http://ubuntuforums.org/showpost.php?p=6341714&postcount=9](http://ubuntuforums.org/showpost.php?p=6341714&postcount=9)

atleast their has been a change in attitude

a shame many linux open source developers fail to see power of the .deb in attracting a large user base.
Oh well, on the other hand you get a nice alternative soulseek client for free that takes about 5 minutes to set up without a deb. I think my script does it in under a minute :popcorn:

---

### Post by OffHand on 2009-05-30
bump

---

### Post by OffHand on 2009-05-31
up

---

### Post by OffHand on 2009-06-01
bump

---

### Post by pt123 on 2009-06-01
why are you bumping this thread

---

### Post by OffHand on 2009-06-01
> **pt123 said:**
> why are you bumping this thread

To answer your (rhetorical) question: I want people to read it and I do not think a bump every 24 hours is too much and/or not appropriate.

Thanks for the bump though! :popcorn:

---

### Post by OffHand on 2009-06-02
bump

---

### Post by hneto on 2009-06-04
Wow, it's unbelievable but true! Now we're part of the distributed search! 

Thanks for your script, helps to save a bit of time.

[Keep on bumpin'...]

---

### Post by Hated On Mostly on 2009-06-04
The script didn't work for me. Now when I try to launch Nicotine Plus from the menu I get an error.

> 
Error
Could not launch menu item

Failed to execute child process "nicotine" (No such file or directory)

You guys really need to make a deb package. Why the delay? I don't understand developers who are unwilling to package their own programs...

---

### Post by OffHand on 2009-06-05
> **Hated On Mostly said:**
> The script didn't work for me. Now when I try to launch Nicotine Plus from the menu I get an error.



You guys really need to make a deb package. Why the delay? I don't understand developers who are unwilling to package their own programs...

Not unwilling... lack of time. We all have full time jobs or are students who do this in their free time. I will help you later today to try sort out your problem. Did you install N+ from the repositories before running the script?

---

### Post by Hated On Mostly on 2009-06-05
> **OffHand said:**
> Not unwilling... lack of time. We all have full time jobs or are students who do this in their free time. I will help you later today to try sort out your problem. Did you install N+ from the repositories before running the script?

Yes, I have had Nicotine Plus (1.2.9) installed from the repository for quite a while now.

I can run 1.2.12 from source (run nicotine.py), and it uses my settings, but the script did not work for me and disabled the previously working Nicotine menu launcher. It also changed the icon for the Nicotine menu launcher.

---

### Post by OffHand on 2009-06-05
> **Hated On Mostly said:**
> Yes, I have had Nicotine Plus (1.2.9) installed from the repository for quite a while now.

I can run 1.2.12 from source (run nicotine.py), and it uses my settings, but the script did not work for me and disabled the previously working Nicotine menu launcher. It also changed the icon for the Nicotine menu launcher.

That's weird. A few others and I have tested it without any issues. Do you have a nicotine+ folder in /opt?

---

### Post by Hated On Mostly on 2009-06-05
> **OffHand said:**
> That's weird. A few others and I have tested it without any issues. Do you have a nicotine+ folder in /opt?

No I do not have a nicotine+ in /opt.

---

### Post by OffHand on 2009-06-05
> **Hated On Mostly said:**
> No I do not have a nicotine+ in /opt.

I suggest you run it again. My guess is it didn't download or extract it properly, but did create the links to where nicotine was supposed to be found.

---

### Post by Hated On Mostly on 2009-06-05
I reinstalled Nicotine through Synaptic and ran the script again. Now my menu link works again and I have a folder in /opt.

Thanks

---

### Post by OffHand on 2009-06-05
> **Hated On Mostly said:**
> I reinstalled Nicotine through Synaptic and ran the script again. Now my menu link works again and I have a folder in /opt.

ThanksMy pleasure. I hope you enjoy it :popcorn:

---

### Post by dragos240 on 2009-06-05
> **OffHand said:**
> We have just released a new version of Nicotine+ with tons of bug fixes. Also we now have a brand spanking new OS X installer (drag 'n drop)!

Download it from [our website]("http://www.nicotine-plus.org/")!

[CHANGELOG]("http://www.nicotine-plus.org/browser/trunk/nicotine%2B/doc/CHANGELOG")

I made a script that will install the latest nicotine release (into /opt) while keeping your install from the repository. Run the script from your home folder.```
sudo sh versionbump_nicotine.sh
```How to revert back to the version from the repositories
```

sudo rm /usr/bin/nicotine
sudo dpkg-divert --rename --remove /usr/bin/nicotine
sudo rm -r /opt/nicotine+-*

```

Mind telling me what it is?

---

### Post by OffHand on 2009-06-05
> **dragos240 said:**
> Mind telling me what it is?
What do you want to know?

---

### Post by Hated On Mostly on 2009-06-06
> **OffHand said:**
> We have just released a new version of Nicotine+ with tons of bug fixes. Also we now have a brand spanking new OS X installer (drag 'n drop)!

Download it from [our website]("http://www.nicotine-plus.org/")!

[CHANGELOG]("http://www.nicotine-plus.org/browser/trunk/nicotine%2B/doc/CHANGELOG")

I made a script that will install the latest nicotine release (into /opt) while keeping your install from the repository. Run the script from your home folder.```
sudo sh versionbump_nicotine.sh
```

How to revert back to the version from the repositories
```

sudo rm /usr/bin/nicotine
sudo dpkg-divert --rename --remove /usr/bin/nicotine
sudo rm -r /opt/nicotine+-*

```


You should add a command to this post to make the script executable.

```
sudo chmod +x versionbump_nicotine.sh
```

---

### Post by OffHand on 2009-06-06
> **Hated On Mostly said:**
> You should add a command to this post to make the script executable.

```
sudo chmod +x versionbump_nicotine.sh
```
Added... Cheers!

---

### Post by BrMBr on 2009-06-09
Hi!

Could you please change the script a bit or give me some instructions? _I don't wanna keep the repositories version, only the updated one_.

How can I put the new version in the same folder it's already in? I don't want it to be inside /opt and don't care to burn the old version.

Thanks!!! :D

PS. I'm a bit noob using Linux, so please be patient. O:)

---

### Post by OffHand on 2009-06-09
> **BrMBr said:**
> Hi!

Could you please change the script a bit or give me some instructions? _I don't wanna keep the repositories version, only the updated one_.

How can I put the new version in the same folder it's already in? I don't want it to be inside /opt and don't care to burn the old version.

Thanks!!! :D

PS. I'm a bit noob using Linux, so please be patient. O:)
Please follow these [instructions]("http://ubuntuforums.org/showpost.php?p=1698178&postcount=146")

Pretty straight forward ;)

p.s. If you are new to linux/ubuntu I recommend using the script method. That's the proper way of doing it.

---

### Post by BrMBr on 2009-06-09
It worked. Thank you very much! ):P

---

### Post by RiceMonster on 2009-06-09
Got the updated version in the Arch repos a few days ago. Thanks for your hard work. I don't know if this was arch specific, but I had to edit the .desktop file and change the execute command to "nicotine.py" rather than just "nicotine" so it would launch correctly from the Xfce menu.

> **dragos240 said:**
> Mind telling me what it is?

It's a soulseek client.

---

### Post by Eisenwinter on 2009-06-23
I just grab the source and edit the directory name in the Openbox menu.

---

### Post by h8uthemost on 2009-07-04
> **RiceMonster said:**
> Got the updated version in the Arch repos a few days ago. 

How did you get the latest version in synaptics? I've tried doing the instructions on the site, and using the script, and neither worked. So installing from the repos is my best bet.

Thanks.

---

### Post by smdofjmdsfjoiez on 2009-07-07
Nicotine deb here:
[http://packages.debian.org/unstable/net/nicotine]("http://packages.debian.org/unstable/net/nicotine")

---

### Post by OffHand on 2009-07-07
> **smdofjmdsfjoiez said:**
> Nicotine deb here:
[http://packages.debian.org/unstable/net/nicotine]("http://packages.debian.org/unstable/net/nicotine")

Nice find! I have updated my post...

---

### Post by BrMBr on 2009-07-07
> **smdofjmdsfjoiez said:**
> Nicotine deb here:
[http://packages.debian.org/unstable/net/nicotine](http://packages.debian.org/unstable/net/nicotine)

Awesome!!! Thank you!!! =D>

Is it possible to add that debian.org to repository? I noticed they have a repository there, but it's not for Ubuntu.

Thanks!

---

### Post by aliencam on 2009-07-10
> **BrMBr said:**
> Awesome!!! Thank you!!! =D>

Is it possible to add that debian.org to repository? I noticed they have a repository there, but it's not for Ubuntu.

Thanks!

You can, 
```

deb http://ftp.de.debian.org/debian sid main 
```

the above is the apt source line, but I would STRONGLY recommend against it, because then you will have all of the packages from Debian Sid instead of the versions in Ubuntu Jaunty.  This will cause major dependencies and library errors (google "adding debian repos to ubuntu" and you will find people who break stuff)

---

### Post by BrMBr on 2009-07-11
Got it! Thanks!

---

### Post by maxol on 2009-07-19
ubuntu jaunty 64

nicotine_1.2.12+dfsg-1_all.deb

[COLOR="Red"]Error: Dependency is not satisfiable: python-support (>= 0.90.0)[/COLOR]

any ideas?

---

### Post by BrMBr on 2009-07-19
> **maxol said:**
> ubuntu jaunty 64

nicotine_1.2.12+dfsg-1_all.deb

[COLOR=Red]Error: Dependency is not satisfiable: python-support (>= 0.90.0)[/COLOR]

any ideas?

Hi!

I had the same problem, but the solution is quite simple. Just get python-support here:

_**[http://packages.debian.org/sid/python-support](http://packages.debian.org/sid/python-support)**_

If you have problem with any other dependencies, notice that you can download 'em all from Nicotine's page. The links are all there:

_**[http://packages.debian.org/unstable/net/nicotine](http://packages.debian.org/unstable/net/nicotine)**_

I hope it helps :D

---

### Post by maxol on 2009-07-19
Thanks MrMBr

---

### Post by tom957 on 2009-09-05
Thanks for the deb!

---

### Post by OwnName on 2009-09-08
Sorry for the ignorance, but I can't find any help googling. So, the debian package provided is missing the new version of python-support (>= 0.90.0). Once I download the 1.0.3 version, I have an archive (.tar.gz) and a debian source (.dsc) package. How can I install it then? Please be redundantly explicit, thanks! ^___^

---

### Post by OffHand on 2009-09-08
> **OwnName said:**
> Sorry for the ignorance, but I can't find any help googling. So, the debian package provided is missing the new version of python-support (>= 0.90.0). Once I download the 1.0.3 version, I have an archive (.tar.gz) and a debian source (.dsc) package. How can I install it then? Please be redundantly explicit, thanks! ^___^

You need the deb file unless you have a compile fetish :P

[Click here]("http://packages.debian.org/sid/python-support")

---

### Post by OwnName on 2009-09-08
Actually, I'd like to know at least a little bit about compiling them. But probably you're right! ;-)
Still, for blind like me, I missed that on the package page, there is "Download python-support", and there the "all" under "architecture" will link you to the download page of the debian package:

[http://packages.debian.org/sid/all/python-support/download](http://packages.debian.org/sid/all/python-support/download)

from there, install it, then install the debian for nicotine. Works nicely. Sweet!  ^___^

---

