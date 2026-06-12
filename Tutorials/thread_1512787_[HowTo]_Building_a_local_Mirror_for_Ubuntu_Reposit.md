---
title: "[HowTo] Building a local Mirror for Ubuntu Repositories."
date: 2010-06-18
forum: Tutorials
---

### Post by pricetech on 2010-06-18
Let me begin with the following;
This is the process that worked for me using bits and pieces of information gathered from sources too numerous to mention, and a lot of trial and error.  I have been able to successfully replicate the process and the results.
I do not and will not suggest that this is "the" way to build a mirror, only that it is "a" way to build one that has been proven to work.

I want to thank forum member and colleague lykwydchykyn for his input, advice, and for critiquing this tutorial for me before submitting it.

====================

Begin by determining where you want your repositories to reside.  You'll need plenty of drive space.  Just as an example I'm mirroring Ubuntu 10.04 Lucid Lynx; 32 bit, packages only - no source code, all repositories and I'm using almost 40 gigs of space.

I'm using my mirror as the example for this tutorial and assuming your mirror will be used internally, not offered as an official mirror.

Start by installing apt-mirror and apache2:
System &#8211; Administration &#8211; Synaptic Package Manager.
Searching for apt-mirror then apache2 will give you the packages you need.
If you prefer to install using the terminal:
```

apt-get install apt-mirror apache2

```

Back up the configuration files:
```

sudo cp /etc/apt/mirror.list /etc/apt/mirror.list.orig
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
sudo cp /etc/cron/apt-mirror /etc/cron/apt-mirror.orig
sudo cp /var/spool/apt-mirror/var/postmirror.sh /var/spool/apt-mirror/var/postmirror.sh.orig

```
This can also be done without the terminal by opening each file in your chosen text editor (gedit for example) and choosing &#8220;save as&#8221; to place the backup copy in your home folder.

Now edit the files.  The examples use nano, but gedit can also be used by invoking it within a terminal using gksudo.

Starting with mirror.list:
```

sudo nano /etc/apt/mirror.list

```
The config section of the file should not require any editing.
For the most part, the repositories section should be okay with its default entries as well.  You might want to add the partner repository by adding this line:
```

deb http://archive.canonical.com/ubuntu lucid partner

```
You might also want to pull your security updates from security.ubuntu.com which would require this modification:
```

deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 

```
You can also remove or comment out the lines dealing with source code if you don't expect to need or use them.  You can always add repositories later if you want.  The time it takes to populate your mirror after adding something is less than the initial population of your mirror, so you can start with the minimum and add more later as the need arises.

Add a couple of lines to the &#8220;clean&#8221; section to clean up the extra repositories if you added or modified them as above:
```

clean http://archive.ubuntu.com/ubuntu
clean http://security.ubuntu.com/ubuntu
clean http://archive.canonical.com/ubuntu

```

Now you can run apt-mirror for the first time.  You might want to wait on this step since it will take a while for your mirror to build, overnight for example.  Also note that apt-mirror should be run as the user apt-mirror.
```

sudo su apt-mirror
apt-mirror

```
You'll see it working, but it will appear slow.

Once the mirror is populated, link the repository to the web server:
```

sudo ln -s /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu /var/www/ubuntu
sudo ln -s /var/spool/apt-mirror/mirror/security.ubuntu.com/ubuntu /var/www/security
sudo ln -s /var/spool/apt-mirror/mirror/archive.canonical.com/ubuntu/ var/www/canonical

```
NOTE: Only the first entry is necessary if you don't add or modify repositories.

Now edit postmirror.sh to invoke the clean script:
```

sudo nano /var/spool/apt-mirror/var/postmirror.sh

```
Add this line:
```

/var/spool/apt-mirror/var/clean.sh

```

Then make both scripts executable:
```

sudo chmod u+x /var/spool/apt-mirror/var/clean.sh
sudo chmod u+x /var/spool/apt-mirror/var/postmirror.sh

```

Finally, make apt-mirror an automated task:
```

sudo nano /etc/cron.d/apt-mirror

```
and remove the comment from the last line.



Moving to the client side:
Edit the sources.list file that will be used to access the mirror.
```

sudo nano /etc/apt/sources.list

```
The example below assumes using the mirror from the computer that hosts it.  Using it from other computers on the network simply requires changing the IP address from 127.0.0.1 to whatever IP address is assigned to the mirror host.
```

deb http://127.0.0.1/ubuntu lucid main restricted universe multiverse
deb http://127.0.0.1/ubuntu lucid-updates main restricted universe multiverse
deb http://127.0.0.1/ubuntu lucid-backports main restricted universe multiverse
deb http://127.0.0.1/ubuntu lucid-proposed main restricted universe multiverse
deb http://127.0.0.1/security lucid-security main restricted universe multiverse
deb http://127.0.0.1/canonical lucid partner

```

On a side note, I've seen it recommended a couple of places that you pull your security updates from their original source rather than a mirror.  If you choose to do that you want to leave this line for lucid-security unchanged:
```

deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse

```

---

### Post by Bertus_Nel on 2010-07-20
Hi Pricetech

Awesome "How To" - I have a quick question though.

I setup a Karmic mirror for our network - we are starting to upgrade to Lucid, is there a way that the mirror can download updates for Lucid aswell? Pointless downloading 60 Gig and then upgrade to 10.04 and all 9.04 updates (all 60 Gigs) wont be used  -So what Im coming at is - Keep the mirror on 9.04 with 10.04 updates aswell. Can this be done?

Thanks

B

---

### Post by k3lt01 on 2010-07-20
Yes it can be done. Basically you will need to structure your mirror exactly the same way as the official Ubuntu mirrors are setup. So you will need the relevant files from archive.ubuntu.com for 10.04.

Check out the attached screenshots to see how the mirror should look.

When downloading the Lucid files you have 2 options, if you dont want to lose karmic you can download the Lucid files to a separate folder and then transfer them to your mirror. Th other thing you can do is adjust your download script to have both Karmic and Lucid that way they will both download and you wont lose Karmic. I recommend you look at [this thread]("http://ubuntuforums.org/showthread.php?t=352460") as well.

Once you have all the files downloaded and placed into the appropriate places adjust your settings to Lucid and you will be ok to go.

---

### Post by pricetech on 2010-07-20
Thanks for jumping in k3.

Yes you can set up your mirror for more than one version of Ubuntu.  All you have to do is add the lines in the mirror.list file to create the new archives on your local mirror and point your clients to it.  Basically, just duplicate the steps, substituting the "new" version for the "old" version.

---

### Post by km0r3 on 2010-07-20
Very helpful tutorial! This has helped me to save a lot of bandwidth as I'm having quite a few Ubuntu machines at home.

Thanks

---

### Post by pricetech on 2010-07-22
You're welcome.

---

### Post by reaxion on 2010-08-25
It seems apt-mirror doesn't generate the indices, ls-lR.gz or the project dirs required for me to install directly from CDs such as the minimal CD and stuff...

Is there a simple way to get these to generate, or do I need to rsync them every time I do an apt-mirror?

---

### Post by pricetech on 2010-08-26
I haven't attempted anything involving CDs.  There are a couple of tutorials in the forums that address that specifically.  You might try search for "Ubuntu CD" or "Ubuntu DVD" and see if that gives you one of those.

---

### Post by oneloveamaru on 2010-08-31
I have a 64bit Lucid server but I also want to download 32bit Lucid packages for the Desktops, any idea on how to do that?

---

### Post by pricetech on 2010-08-31
It's not fresh in my brain, but as I recall you can do that by specifying the architecture in your mirror.list file.  I'd have to look it up to say how, but it's in the documentation.

---

### Post by oneloveamaru on 2010-08-31
Thanks, found that right after I posted. I'll have to look up the syntax but I'm sure the man page will tell me. :)

---

### Post by pricetech on 2010-08-31
> **oneloveamaru said:**
> Thanks, found that right after I posted. I'll have to look up the syntax but I'm sure the man page will tell me. :)

Cool. Much success with it and feel free to post on this thread any tips you learn while doing.

---

### Post by mccartyj on 2011-03-25
Excellent How-To, thank you for posting it. :guitar:

Do you need to use the deb-amd64 and deb-i386 sources to get both repositories, or is that only for older distributions (I only see it on older how-tos).

Thanks!

---

### Post by pricetech on 2011-03-25
Seems forever since I wrote that tutorial, but I'm pretty sure you do.  I didn't include it since I was only supporting and building for a single processor architecture.

Best I recall you add lines for each repo that start with "deb-amd64" instead of just "deb".

I hope I'm remembering right.

---

### Post by pricetech on 2011-03-26
From the man page for sources.list:

>  distribution may also contain a variable, $(ARCH) which expands to the Debian architecture (i386, m68k, powerpc, ...) used on the system. This permits architecture-independent sources.list files to be used. In general this is only of interest when specifying an exact path, APT will automatically generate a URI with the current architecture otherwise.


I haven't done it, so I don't know about any "gotchas" that you might encounter.

Have fun with it and do please post back anything you learn for the benefit of others.

If you decide to write a new tutorial, feel free to use anything from mine that saves you time.

Joe

---

### Post by mccartyj on 2011-03-28
I downloaded the repos this weekend and yes, you do need to specify deb-i386 and/or deb-amd64. I ran apt-mirror on a 64-bit machine and just plain "deb ..." only got the 64-bit repos. I've update my mirror.list to include "deb-i386" and "deb-amd64" and I'll see what happens tonight when I update it.

Thanks again for your help.

---

### Post by rmaultz on 2012-09-14
would it be possible  to create a shell script  with all commands  and  instructions  for  automated  server installs 

need a script  to set up 12 ubuntu servers as  load balancers

---

