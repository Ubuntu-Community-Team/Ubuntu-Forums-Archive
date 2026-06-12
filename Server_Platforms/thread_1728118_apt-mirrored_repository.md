---
title: "apt-mirrored repository"
date: 2011-04-13
forum: Server Platforms
---

### Post by MakOwner on 2011-04-13
I have it downloaded, I can browse the repository via http on port 80.

I try doing an install from the minimal installation ISO and enter the hostname:port number of the host with the repository, and then it asks for a directory and defaults to /ubuntu - which is the directory shared from the repository: [http://localmachine/ubuntu](http://localmachine/ubuntu)

Installation fails stating it can't find the distribution.  

I can't find any documentation on exactly what directory or files the installer is looking for.  

Can someone point me in the right direction?

---

### Post by MakOwner on 2011-04-13
IS this in the wrong place, or no one uses their own repo?

---

### Post by Wobblybob on 2011-04-13
I've never had the whole apt repo mirrored but i do use apt-cacher-ng to save all the packages once as the first Pc downloads it so others pull the package from apt-cache rather than download again. If this sounds like what you need you could check out my blog entry here.

[[COLOR="Navy"]http://myubuntublog.wordpress.com/2009/05/17/an-apt-server-using-apt-cacher/[/COLOR]]("http://myubuntublog.wordpress.com/2009/05/17/an-apt-server-using-apt-cacher/")

---

### Post by MakOwner on 2011-04-13
> **Wobblybob said:**
> I've never had the whole apt repo mirrored but i do use apt-cacher-ng to save all the packages once as the first Pc downloads it so others pull the package from apt-cache rather than download again. If this sounds like what you need you could check out my blog entry here.

[[COLOR="Navy"]http://myubuntublog.wordpress.com/2009/05/17/an-apt-server-using-apt-cacher/[/COLOR]]("http://myubuntublog.wordpress.com/2009/05/17/an-apt-server-using-apt-cacher/")

I'll look this over and maybe it will help, but I'm not looking to hold the repo for updates - I want to hold it so I can do a fresh install over the local network and not have to download from an external mirror.  This *shouldn't* be this hard, but it damn sure is turning into a fairly difficult thing.

I can find a lot of stuff on mirroring the repos, updating from the mirror, but nothing so far on installing from the mirror.

Looks like it would be easier just to create a custom installation ISO.  Sure hope that isn't the case 

](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by tgm4883 on 2011-04-13
> **MakOwner said:**
> I'll look this over and maybe it will help, but I'm not looking to hold the repo for updates - I want to hold it so I can do a fresh install over the local network and not have to download from an external mirror.  This *shouldn't* be this hard, but it damn sure is turning into a fairly difficult thing.

I can find a lot of stuff on mirroring the repos, updating from the mirror, but nothing so far on installing from the mirror.

Looks like it would be easier just to create a custom installation ISO.  Sure hope that isn't the case 

](*,)](*,)](*,)](*,)](*,)](*,)

I use to mirror the entire repo via rsync, but now I just use apt-mirror and get the parts I'm interested in.

You need to point the client at the directory on the server that has the dist/ and pool/ directories. If you fire up a web browser and go to 

```
http://localhost/ubuntu/
```

You should see the dist/ and pool/ subdirectories. If you do not, you either are pointed at the wrong directory, or you have a permissions issue.

Keep in mind, that by default, apt-mirror only downloads the same architecture packages as the server it is installed on. To gather other architectures, you need to setup your mirror.list file with something similar to

```
deb-i386 http://ubuntu.osuosl.org/ubuntu lucid main restricted universe multiverse
deb-amd64 http://ubuntu.osuosl.org/ubuntu lucid main restricted universe multiverse
```

---

### Post by MakOwner on 2011-04-13
> **tgm4883 said:**
> I use to mirror the entire repo via rsync, but now I just use apt-mirror and get the parts I'm interested in.

You need to point the client at the directory on the server that has the dist/ and pool/ directories. If you fire up a web browser and go to 

```
http://localhost/ubuntu/
```

You should see the dist/ and pool/ subdirectories. If you do not, you either are pointed at the wrong directory, or you have a permissions issue.

Keep in mind, that by default, apt-mirror only downloads the same architecture packages as the server it is installed on. To gather other architectures, you need to setup your mirror.list file with something similar to

```
deb-i386 http://ubuntu.osuosl.org/ubuntu lucid main restricted universe multiverse
deb-amd64 http://ubuntu.osuosl.org/ubuntu lucid main restricted universe multiverse
```

I have setup apt-mirror, downloaded the repositories, set up daily updates. I linked the repo under the apache root as suggested in the apt-mirror information and I can browse to the host and browse the directories of the repo.

```

Index of /ubuntu
[ICO]	Name	Last modified	Size	Description
[DIR]	Parent Directory	 	- 	 
[DIR]	dists/	07-Apr-2011 20:27 	- 	 
[DIR]	pool/	07-Apr-2011 21:41 	- 	 
Apache/2.2.14 (Ubuntu) Server at pe350-2 Port 80

```
 
Now I want to boot up with the minimal installation CD and point to the repository when prompted for the mirror by choosing the manual entry option. I can get to the point the installer complains about "bad release files".

And I only get that when I add dists/lucid on to the /ubuntu directory the installer adds by default.

---

### Post by MakOwner on 2011-04-13
So, I'm looking at the repository how to: [http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html#release](http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html#release)

Will this work for Ubuntu?

If so, I need this to build the Packages.gz file, but there are already packages files in the stuff apt-mirror downloaded.

dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz

---

### Post by tgm4883 on 2011-04-13
> **MakOwner said:**
> I have setup apt-mirror, downloaded the repositories, set up daily updates. I linked the repo under the apache root as suggested in the apt-mirror information and I can browse to the host and browse the directories of the repo.

```

Index of /ubuntu
[ICO]	Name	Last modified	Size	Description
[DIR]	Parent Directory	 	- 	 
[DIR]	dists/	07-Apr-2011 20:27 	- 	 
[DIR]	pool/	07-Apr-2011 21:41 	- 	 
Apache/2.2.14 (Ubuntu) Server at pe350-2 Port 80

```
 
Now I want to boot up with the minimal installation CD and point to the repository when prompted for the mirror by choosing the manual entry option. I can get to the point the installer complains about "bad release files".

And I only get that when I add dists/lucid on to the /ubuntu directory the installer adds by default.

Odd. I downloaded the minimal ISO and couldn't connect it to my apt-mirror repo either. Perhaps the minimal ISO doesn't like the apt-mirror structure?

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> Odd. I downloaded the minimal ISO and couldn't connect it to my apt-mirror repo either. Perhaps the minimal ISO doesn't like the apt-mirror structure?

I found this, which led me down the path to another post, which at least has a method of getting a copy of the repository and the needed release and authentication files.   It doesn't use apt-mirror, however.  Not sure what the hell apt-mirror is used for as it doesn't appear to actually mirror the repository in a usable state.  debmirror seems to mirror it and copy down the appropriate key files, however, if you have already downloaded everything with apt-mirror, you'll basically be starting over. <sigh>


[http://ubuntuforums.org/showthread.php?t=352460&highlight=debmirror](http://ubuntuforums.org/showthread.php?t=352460&highlight=debmirror)

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> I found this, which led me down the path to another post, which at least has a method of getting a copy of the repository and the needed release and authentication files.   It doesn't use apt-mirror, however.  Not sure what the hell apt-mirror is used for as it doesn't appear to actually mirror the repository in a usable state.  debmirror seems to mirror it and copy down the appropriate key files, however, if you have already downloaded everything with apt-mirror, you'll basically be starting over. <sigh>


[http://ubuntuforums.org/showthread.php?t=352460&highlight=debmirror](http://ubuntuforums.org/showthread.php?t=352460&highlight=debmirror)

It's in a usable state for me. Likely it's just something that the minimal ISO is checking for that doesn't exist. I honestly didn't even know there was a minimal ISO

---

### Post by tgm4883 on 2011-04-14
So a little searching found this link

[https://help.ubuntu.com/community/Installation/LocalNet#Advanced:](https://help.ubuntu.com/community/Installation/LocalNet#Advanced:) Network install using apt-mirror

I haven't tested it, but it makes sense

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> It's in a usable state for me. Likely it's just something that the minimal ISO is checking for that doesn't exist. I honestly didn't even know there was a minimal ISO

So, using your mirror you can boot up an installation CD/DVD and point it at your local repository and it will install?

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> So, using your mirror you can boot up an installation CD/DVD and point it at your local repository and it will install?

I was actually saying that I am able to do daily updates with it just fine. I hadn't tested an install from the minimal ISO. However, I just fired up a minimal ISO in a virtual box machine and pointed it to my local repository and it is installing just fine. All I had to do was configure apt-mirror correctly.

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> I was actually saying that I am able to do daily updates with it just fine. I hadn't tested an install from the minimal ISO. However, I just fired up a minimal ISO in a virtual box machine and pointed it to my local repository and it is installing just fine. All I had to do was configure apt-mirror correctly.

OK, I'll bite -- what is the magic in apt-mirror I'm missing?
This is my mirror.list file and this will get everything down except source.  

I set up a link for the webserver on that host :
/var/www/ubuntu -> /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu

I boot from the minimal installer and point it at my webserver

[http://localrepo/ubuntu](http://localrepo/ubuntu) 

and the installer says it isn't available or responding.  I point it down into the lucid or lucid/main directories and it changes the message to invalid packages files.

I think I'd rather use apt-mirror than what I'm trying with debmirror right now.  I'm 36% into the debmirror downloads. 

```

cat /etc/apt/mirror.list 
############# config ##################
#
set base_path    /var/spool/apt-mirror
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set postmirror_script $var_path/postmirror.sh
set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse 
#deb http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse

#deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse

```

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> OK, I'll bite -- what is the magic in apt-mirror I'm missing?
This is my mirror.list file and this will get everything down except source.  

I set up a link for the webserver on that host :
/var/www/ubuntu -> /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu

I boot from the minimal installer and point it at my webserver

[http://localrepo/ubuntu](http://localrepo/ubuntu) 

and the installer says it isn't available or responding.  I point it down into the lucid or lucid/main directories and it changes the message to invalid packages files.

I think I'd rather use apt-mirror than what I'm trying with debmirror right now.  I'm 36% into the debmirror downloads. 

```

cat /etc/apt/mirror.list 
############# config ##################
#
set base_path    /var/spool/apt-mirror
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set postmirror_script $var_path/postmirror.sh
set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse 
#deb http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse

#deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse

```

Please check the link I posted in post 17

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> Please check the link I posted in post 17

11 in this thread, right?

Down in the apt-mirror section is a link to the how to I used to setup apt-mirror.  Looks like the bit missing from the apt-mirror was the section about debain-installer.


I'm going to stop the debmirror download and try apt-mirror again.

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> 11 in this thread, right?

Down in the apt-mirror section is a link to the how to I used to setup apt-mirror.  Looks like the bit missing from the apt-mirror was the section about debain-installer.


I'm going to stop the debmirror download and try apt-mirror again.

Heh yea 11, cause 17 is this thread which is from the future!

[https://help.ubuntu.com/community/Installation/LocalNet#Advanced:](https://help.ubuntu.com/community/Installation/LocalNet#Advanced:)


But yea, as soon as I did that I was able to download the extra 100 MB and it worked fine

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> Heh yea 11, cause 17 is this thread which is from the future!

[https://help.ubuntu.com/community/Installation/LocalNet#Advanced:](https://help.ubuntu.com/community/Installation/LocalNet#Advanced:)


But yea, as soon as I did that I was able to download the extra 100 MB and it worked fine

Thanks -- I'll give this a shot. I just cranked up apt-mirror and it says it's downloading 42GB ...  

I have a 30 down/30 up fiber connection and I'm only getting about 4MB/s transfer rate.  :/

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> Thanks -- I'll give this a shot. I just cranked up apt-mirror and it says it's downloading 42GB ...  

I have a 30 down/30 up fiber connection and I'm only getting about 4MB/s transfer rate.  :/

hmm, you added exactly what was said in that link didn't you.

If so, that isn't necessary. You just need to add main/debian-installer and restricted/debian-installer to your line. The line I was testing with in mirror.list now looks like this.

```
deb-i386 http://ubuntu.osuosl.org/ubuntu maverick main main/debian-installer restricted restricted/debian-installer  universe multiverse
```

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> hmm, you added exactly what was said in that link didn't you.

If so, that isn't necessary. You just need to add main/debian-installer and restricted/debian-installer to your line. The line I was testing with in mirror.list now looks like this.

```
deb-i386 http://ubuntu.osuosl.org/ubuntu maverick main main/debian-installer restricted restricted/debian-installer  universe multiverse
```

I caught that right after I started it...

I now have as the active lines in the configuration:
```

deb http://archive.ubuntu.com/ubuntu lucid main main/debian-installer restricted restricted/debian-installer
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse 

```


Wonder if it would make any difference if I pointed all of this at us.archive.ubuntu.com?

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> I caught that right after I started it...

I now have as the active lines in the configuration:
```

deb http://archive.ubuntu.com/ubuntu lucid main main/debian-installer restricted restricted/debian-installer
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse 

```


Wonder if it would make any difference if I pointed all of this at us.archive.ubuntu.com?

Well it would download the entire archive again since it would look for a directory named us.archive.ubuntu.com find it didn't exist and create it. 

I actually did something similar when I set mine up. I used apt-mirror with my local rsync mirror, then renamed the directory afterwards.

So if you wanted to use us.archive.ubuntu.com, fix your mirror.list to point to us.archive.ubuntu.com, then rename the archive.ubuntu.com directory to us.archive.ubuntu.com.

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> Well it would download the entire archive again since it would look for a directory named us.archive.ubuntu.com find it didn't exist and create it. 

I actually did something similar when I set mine up. I used apt-mirror with my local rsync mirror, then renamed the directory afterwards.

So if you wanted to use us.archive.ubuntu.com, fix your mirror.list to point to us.archive.ubuntu.com, then rename the archive.ubuntu.com directory to us.archive.ubuntu.com.

It won't make much difference for me, both us.archive and archive both appear to traceroute back to London anyway - if I can read this right.

Minimum of 17 hops...

---

### Post by MakOwner on 2011-04-14
Another question -- in order to include other architectures, do I need to use arch specific lines, or can I just set multiple arch's in the "set defaultarch" line of sources.list?

The man page says the configuration file is well documented in the comments.
I must have missed that one.

Any event, the keyword for the 32 and 64 bit arch's are i386 and amd64, or is it x86_64 these days?

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> Another question -- in order to include other architectures, do I need to use arch specific lines, or can I just set multiple arch's in the "set defaultarch" line of sources.list?

The man page says the configuration file is well documented in the comments.
I must have missed that one.

Any event, the keyword for the 32 and 64 bit arch's are i386 and amd64, or is it x86_64 these days?

To my knowledge, apt-mirror doesn't use sources.list at all, just mirror.list. I have separate lines for each arch I want to download, which doubles my list. I use deb-i386 and deb-amd64

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> To my knowledge, apt-mirror doesn't use sources.list at all, just mirror.list. I have separate lines for each arch I want to download, which doubles my list. I use deb-i386 and deb-amd64

Yea, meant to say mirror.list not sources.list.

After I get the 32bit done, I'm going to test my installation, and if that works, I'm going to try adding the 64bit, then start working on mirroring the other repos that I use.

---

### Post by MakOwner on 2011-04-14
> **MakOwner said:**
> Yea, meant to say mirror.list not sources.list.

After I get the 32bit done, I'm going to test my installation, and if that works, I'm going to try adding the 64bit, then start working on mirroring the other repos that I use.

Ah, damnit.  Still no joy.
I don't see anything about an installer anywhere still.

Using a web browser when I view my repo it looks just like it did in the earlier post I made.

And the output of the apt-mirror command...  So I'm assuming it downloaded the installer, but then removed it??

```

Downloading 25049 archive files using 30 threads...
Begin time: Thu Apr 14 11:29:00 2011
[30]... [29]... [28]... [27]... [26]... [25]... [24]... [23]... [22]... [21]... [20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Thu Apr 14 13:57:15 2011

2.8 GiB in 3572 files and 10 directories can be freed.
Run /var/spool/apt-mirror/var/clean.sh for this purpose.

Removing 3572 unnecessary files [3004473344 bytes]...
[0%]..................................................[13%]..................................................[27%]..................................................[41%]..................................................[55%]..................................................[69%]..................................................[83%]..................................................[97%]........done.

Removing 10 unnecessary directories...
[0%]..........done.

```

---

### Post by tgm4883 on 2011-04-14
It likely downloaded updated packages at the same time and removed old ones.

You should see the debian-installer directories if you go to
[http://localhost/ubuntu/dists/lucid/main/](http://localhost/ubuntu/dists/lucid/main/)
[http://localhost/ubuntu/dists/lucid/restricted/](http://localhost/ubuntu/dists/lucid/restricted/)

Can you post your mirror.list?

---

### Post by MakOwner on 2011-04-14
OK, I have the debian-installer folder under /ubuntu/dists/lucid/restricted and the contents of the folder is just an binary-i386 folder that contains a 0 byte Packages file, a 14 byte Packages.bz2 and a 20 byte Packages.gz.

To say that I'm somewhat frustrated is an understatement.

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> It likely downloaded updated packages at the same time and removed old ones.

You should see the debian-installer directories if you go to
[http://localhost/ubuntu/dists/lucid/main/](http://localhost/ubuntu/dists/lucid/main/)
[http://localhost/ubuntu/dists/lucid/restricted/](http://localhost/ubuntu/dists/lucid/restricted/)

Can you post your mirror.list?

Here's what's in those directories and the mirror.list file.

```

ls -al /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/lucid/main/
total 0
drwxr-xr-x 4 apt-mirror apt-mirror  47 2011-04-14 14:00 .
drwxr-xr-x 6 apt-mirror apt-mirror 121 2011-04-14 14:00 ..
drwxr-xr-x 2 apt-mirror apt-mirror  72 2011-04-14 13:58 binary-i386
drwxr-xr-x 3 apt-mirror apt-mirror  24 2011-04-14 07:56 debian-installer


ls -al /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/lucid/restricted/
total 0
drwxr-xr-x 4 apt-mirror apt-mirror  47 2011-04-14 13:58 .
drwxr-xr-x 6 apt-mirror apt-mirror 121 2011-04-14 14:00 ..
drwxr-xr-x 2 apt-mirror apt-mirror  72 2011-04-14 13:58 binary-i386
drwxr-xr-x 3 apt-mirror apt-mirror  24 2011-04-14 13:58 debian-installer


```



```

$ cat /etc/apt/mirror.list
############# config ##################
#
set base_path    /var/spool/apt-mirror
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set postmirror_script $var_path/postmirror.sh
set run_postmirror 0
set nthreads     30
set _tilde 0
#
############# end config ##############
deb http://archive.ubuntu.com/ubuntu lucid main main/debian-installer restricted restricted/debian-installer
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse 

clean http://archive.ubuntu.com/ubuntu


```

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> Here's what's in those directories and the mirror.list file.

```

ls -al /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/lucid/main/
total 0
drwxr-xr-x 4 apt-mirror apt-mirror  47 2011-04-14 14:00 .
drwxr-xr-x 6 apt-mirror apt-mirror 121 2011-04-14 14:00 ..
drwxr-xr-x 2 apt-mirror apt-mirror  72 2011-04-14 13:58 binary-i386
drwxr-xr-x 3 apt-mirror apt-mirror  24 2011-04-14 07:56 debian-installer


ls -al /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/lucid/restricted/
total 0
drwxr-xr-x 4 apt-mirror apt-mirror  47 2011-04-14 13:58 .
drwxr-xr-x 6 apt-mirror apt-mirror 121 2011-04-14 14:00 ..
drwxr-xr-x 2 apt-mirror apt-mirror  72 2011-04-14 13:58 binary-i386
drwxr-xr-x 3 apt-mirror apt-mirror  24 2011-04-14 13:58 debian-installer


```



```

$ cat /etc/apt/mirror.list
############# config ##################
#
set base_path    /var/spool/apt-mirror
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set postmirror_script $var_path/postmirror.sh
set run_postmirror 0
set nthreads     30
set _tilde 0
#
############# end config ##############
deb http://archive.ubuntu.com/ubuntu lucid main main/debian-installer restricted restricted/debian-installer
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse 

clean http://archive.ubuntu.com/ubuntu


```

Odd, I wonder if the second one of these is causing any issues
```
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse 
```

---

### Post by MakOwner on 2011-04-14
Perhaps the issue is not in the repo, but in the way I'm filling in the url for it?

When prompted for the repository, I'm entering 

[http://local-host-name-that-can-be-resolved](http://local-host-name-that-can-be-resolved)

and then I'm prompted for a directory on the next screen.

The default entry is /ubuntu

I have tried that and also added various levels of subdirectories that are visible to the a desktop web browser.  

I don't even see any failed requests in the apache logs..

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> Odd, I wonder if the second one of these is causing any issues
```
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse 
```

So, I have added universe multiverse to the end of the first line and commented out the second line.

looks like this now:
```

deb http://archive.ubuntu.com/ubuntu lucid main main/debian-installer restricted restricted/debian-installer universe multiverse

```

re-running apt-mirror.


It downloaded 0 new bytes.

---

### Post by MakOwner on 2011-04-14
Any idea where the logging occurs for the installer?
I'm not seeing crap on the console where I'm installing and the syslog has nothing in it. 

the webserver has no evidence the machine that's running the installer ever tried to touch it.

It's days like this that make me bald.

](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> Any idea where the logging occurs for the installer?
I'm not seeing crap on the console where I'm installing and the syslog has nothing in it. 

the webserver has no evidence the machine that's running the installer ever tried to touch it.

It's days like this that make me bald.

](*,)](*,)](*,)](*,)](*,)](*,)

On the repository section of the installer, I just used my IP address, no [http://.](http://.) Then the next section I used /ubuntu/ 

I'd try that

---

### Post by MakOwner on 2011-04-14
aaarrrggghhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh...

On the screen where you manually enter your mirror, you enter the hostname:port.  Only.  No protocol prefix.


Just f*ck me.

---

### Post by tgm4883 on 2011-04-14
> **MakOwner said:**
> aaarrrggghhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh...

On the screen where you manually enter your mirror, you enter the hostname:port.  Only.  No protocol prefix.


Just f*ck me.

So it works now?

---

### Post by MakOwner on 2011-04-14
> **tgm4883 said:**
> On the repository section of the installer, I just used my IP address, no [http://.](http://.) Then the next section I used /ubuntu/ 

I'd try that

I know I can get to the machine with the repo, I had already opened a console and was able to ping and resolve the host name I was using in the entry in the installer. 

No logs, no errors, NOTHING to indicate what was going on.

I am obviously too stupid to operate this stuff.



So,, in the end, it had nothing to do with the repo.  (well, maybe, I didn't have the installer section before, so that was a big issue) but in the end, the entry that you put in for a manual entry doesn't look like the display of the other pre-filled entries.

If you boot up and you select, say the us repository to install from you select an entry with "http://blablahblah"

When you use a local entry, you apparently cannot use the "http://".
I'm guessing the installer doesn't really use what's in the display, it's just a convenient display.  :/




After thoughts :   I am too stupid to operate heavy machinery.  I went back and re-ran the installer and the hosts displayed for the mirrors don't have http:// prepended to them.  I have no idea why that was stuck in my head that I needed to use the protocol identifier.  Perhaps all of the mirror and sources list files set up that require the choice of protocol affected me.  

I have no idea.

I'll leave my stupidity here for someone else to stumble upon and maybe they will learn from my mistakes... :/

---

### Post by tgm4883 on 2011-04-14
Sounds good, you should mark the thread as solved

---

### Post by MakOwner on 2011-04-14
Final solution: 

mirror.list with these lines (these work for me, YMMV)
```

############# config ##################
#
set base_path    /var/spool/apt-mirror
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set postmirror_script $var_path/postmirror.sh
set run_postmirror 0
set nthreads     30
set _tilde 0
#
############# end config ##############
deb http://archive.ubuntu.com/ubuntu lucid main main/debian-installer restricted restricted/debian-installer universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse 

clean http://archive.ubuntu.com/ubuntu

```

symlink from /var/www (default apache web directory on an Ubuntu install) to /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu 

and when using the minimal installaiton ISO, when it prompts you to select the mirror, select the top entry to manually enter the mirror.

If you are using http to serve the repo, you don't even need to enter the port number, just the host name or IP address as reachable by the host on which you are installing.  The next screen will prompt you for a directory, and the default "/ubuntu" worked for me, and the installer loaded.  

First install hasn't completed yet, so we'll see what happens.


There is some stuff with keyrings and what not that I messed with as part of debmirror when trying to get it to work, not sure if that's needed for apt-mirror or not.



This is not that hard to set up -- the hard and EXTREMELY frustrating bit is find all of the scattered bits of information to make it work.  Not being the sharpest tool in the shed doesn't help either!

---

### Post by MakOwner on 2011-04-14
Yet another follow up -- I know I'll be doing this again some day and this is as good a place as any to keep notes!

IF you use a repository like for an installation, be aware that the installer will put your repository in the target machines' sources.list file.  If you have cheaped out as I did, and didn't get the sources along with the binaries, you'll have clean up to do after your first boot of the new machine.  

The installer includes source repositories from your host even if they don't exists, so the first time you run 'apt-get update' you'll see errors until you comment out the repos listed that don't exist.  I'm just updating mine to include the src repos as I have the free space.

And yet another update:


I have added some other repositories and have them working, and updating with apt-mirror.
/etc/apt/mirror.list:

```

############# config ##################
#
set base_path    /var/spool/apt-mirror
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set postmirror_script $var_path/postmirror.sh
set run_postmirror 0
set nthreads     30
set _tilde 0
#
############# end config ##############
deb http://archive.ubuntu.com/ubuntu lucid main main/debian-installer restricted restricted/debian-installer universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse 
#deb http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu lucid partner

deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb-src http://archive.canonical.com/ubuntu lucid partner

## Webmin
deb http://download.webmin.com/download/repository sarge contrib

## Medibuntu
deb http://packages.medibuntu.org/ lucid free non-free 

clean http://archive.ubuntu.com/ubuntu
clean http://download.webmin.com/download/repository 
clean http://packages.medibuntu.org/ 

```


This lets me install from a local repository and after the install, I can add the keys from the original webmin and medibuntu repository and then install in the client directly from my repository.

---

### Post by R.Bucky on 2011-04-16
Think about adding the 64-bit packages as well. It will make your local repo much more useful for scaling your systems, or if you make it public.

---

### Post by MakOwner on 2011-04-16
> **R.Bucky said:**
> Think about adding the 64-bit packages as well. It will make your local repo much more useful for scaling your systems, or if you make it public.


This is roughly 94GB of disk space.
Anyone know if the installer has a source repo?

```

############# config ##################
#
set base_path    /var/spool/apt-mirror
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
set defaultarch  i386
set postmirror_script $var_path/postmirror.sh
set run_postmirror 0
set nthreads     30
set _tilde 0
#
############# end config ##############
# 32 bit
deb http://archive.ubuntu.com/ubuntu lucid main main/debian-installer restricted restricted/debian-installer universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse 
#deb http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu lucid partner
# 64 bit
deb-amd64 http://archive.ubuntu.com/ubuntu lucid main main/debian-installer restricted restricted/debian-installer universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
#deb-amd64 http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb-amd64 http://archive.canonical.com/ubuntu lucid partner

# Source code
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb-src http://archive.canonical.com/ubuntu lucid partner

## Webmin
deb http://download.webmin.com/download/repository sarge contrib
deb-amd64 http://download.webmin.com/download/repository sarge contrib
## Medibuntu
deb http://packages.medibuntu.org/ lucid free non-free 
deb-amd64 http://packages.medibuntu.org/ lucid free non-free


clean http://archive.ubuntu.com/ubuntu
clean http://download.webmin.com/download/repository 
clean http://packages.medibuntu.org/ 

```

---

### Post by R.Bucky on 2011-04-16
To which installer to do refer?

---

### Post by MakOwner on 2011-04-16
> **R.Bucky said:**
> To which installer to do refer?

This one:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main **main/debian-installer** restricted **restricted/debian-installer** universe multiverse

When I put in a deb-src for this it fails.  Is there an equivalent?

---

### Post by R.Bucky on 2011-04-16
Hmm. You know, I don't have any of the -src listings in my mirror. This is my mirror.list at [http://nwlinux.com/single_pages/mirror.list]("http://nwlinux.com/single_pages/mirror.list") 

It never came to mind that I would want/need the deb-src. Everything that I need to operate a successful mirror is on the mirror. Can you explain why you might want it?

---

### Post by tgm4883 on 2011-04-16
You need it if you want to download the source code for a package. You would do that via

```
apt-get source <package name>
```

The majority of users don't ever use these (or rarely do).

---

### Post by R.Bucky on 2011-04-16
@tgm4883 - thanks for clarifying. I have never used that function in the years that I have been using Ubuntu. You learn something new everyday...

---

### Post by MakOwner on 2011-04-16
> **R.Bucky said:**
> @tgm4883 - thanks for clarifying. I have never used that function in the years that I have been using Ubuntu. You learn something new everyday...

I'm not sure I'll ever *need* any of this - I wanted the repository because I have done installation/reinstallation of servers probably 50 - 60 times over the last few weeks.  By having the repo locally I cut down the transfer time, and hopefully I'm saving someone, somewhere a bit of bandwidth.

That said, the next thing I'll be putzing around with is a custom installation image.  I want to fill in the variables that are usually needed during an install so I don't have to answer prompts for the same thing every time.

And I'm absolutely sure I'm re-inventing the wheel, but I learn (well, maybe, some days..) when I do this.


So, the short answer is "because I can" :)

---

### Post by R.Bucky on 2011-04-16
Good enough for me. "Because I can" is a great answer :-)

I am adding the deb-src entries to my mirror as well. I'll see how that works out...

---

### Post by MakOwner on 2011-04-16
> **R.Bucky said:**
> Good enough for me. "Because I can" is a great answer :-)

I am adding the deb-src entries to my mirror as well. I'll see how that works out...

It's consumed about 94GB of space here so be prepared :)

---

### Post by R.Bucky on 2011-04-16
Curious, mine only came out to 36.3GB when adding the deb-src entries???

[http://nwlinux.com/ubuntu-apt-get-deb-src/]("http://nwlinux.com/ubuntu-apt-get-deb-src/")

---

### Post by MakOwner on 2011-04-16
> **R.Bucky said:**
> Curious, mine only came out to 36.3GB when adding the deb-src entries???

[http://nwlinux.com/ubuntu-apt-get-deb-src/]("http://nwlinux.com/ubuntu-apt-get-deb-src/")

I did i386 and amd64 - binary and source.

I have maybe two or three 64 bit machines as of right now, but two of them are ESXi servers, so I figured what the heck...

---

### Post by tgm4883 on 2011-04-16
IMO, a better (different?) way to save bandwidth is to use squid-deb-proxy (and squid-deb-proxy-client). This doesn't do a periodic download, which is the reason I use apt-mirror on mine (slow bandwidth :( )

The way squid-deb-proxy works is like apt-cacher-ng, with one huge improvement.

1) You install squid-deb-proxy on a server. It will cache downloaded deb packages when requested. Also install squid-deb-proxy-client so the server will use the proxy server for updates (itself being the proxy server)

2) You install squid-deb-proxy-client on any other machine you want to update from the server. The way this differs from apt-cacher-ng is auto-configuration. You don't have to do any configuration of apt. When you do an apt-get update on your machine, it will look for the squid proxy (via avahi) and update from it if it finds it. If it doesn't find one (like if you had a laptop and were somewhere offsite) then it would download from the internet.


For the OP though, I don't think that would work as the mini iso likely doesn't have squid-deb-proxy-client. Just wanted to mention this here for future users.

---

