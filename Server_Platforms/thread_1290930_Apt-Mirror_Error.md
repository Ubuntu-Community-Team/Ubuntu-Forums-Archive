---
title: "Apt-Mirror Error"
date: 2009-10-14
forum: Server Platforms
---

### Post by HighlyDubious on 2009-10-14
I've installed apt-mirror (per the instructions I found from several how-to's on the web), and configured my mirror.list file to point to the nearest mirror.

But when I run apt-mirror, it will download the initial index, then fail with the following error message

```
ima@Sloe-Server:~$ sudo apt-mirror /etc/apt/mirror.list
[sudo] password for ima:
Downloading 140 index files using 30 threads...
Begin time: Wed Oct 14 02:05:01 2009
[30]... [29]... [28]... [27]... [26]... [25]... [24]... [23]... [22]... [21]... [20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]...
End time: Wed Oct 14 02:05:22 2009

Proceed indexes: [SSsh: [ubuntu.osuosl.org/ubuntu//dists/jaunty-updates/restricted/source/Sources.gz]("http://ubuntu.osuosl.org/ubuntu//dists/jaunty-updates/restricted/source/Sources.gz"): No such file or directory
apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 390.

```I can see that the problem is an extra '**/**' between '**ubuntu//dists**' but I don't know to tell apt-mirror to stop putting it in there.

Here is my edited mirror.list: (note, there is no '**/**' after '**ubuntu**'  in the url's below)

```
ima@Sloe-Server:~$ more /etc/apt/mirror.list
############# config ##################
#
set base_path   /home/ima/Apt-Mirror
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privileges
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set defaultarch amd64
set nthreads     30
set _tilde 0
#
############# end config ##############

deb [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty main restricted universe multiverse
deb [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty-updates main restricted universe multiverse
deb [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty-backports main restricted universe multiverse
deb [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty-security main restricted universe multiverse
deb [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty-proposed main restricted universe multiverse

deb-src [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty main restricted universe multiverse
deb-src [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty-updates main restricted universe multiverse
deb-src [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty-backports main restricted universe multiverse
deb-src [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty-security main restricted universe multiverse
deb-src [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) jaunty-proposed main restricted universe multiverse

clean [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu)

```Any help will be appreciated.

---

### Post by HighlyDubious on 2009-10-15
Bump.

I've spent some time trying to figure out the problem.

I've discovered that 'apt-mirror' is a perl script, stored in /user/bin. My own skills in perl are fairly weak, but it appears that my initial guess regarding an extra '**/**' was ***NOT*** correct.

As far as I can see, that extra '**/**' is only in the error message printed to the screen, and is stripped out when the actual URL request is made by apt-mirror.

In addition, the failure is occurring after apt-mirror has already accessed the following directories.

```

http://ubuntu.osuosl.org/ubuntu/dists/jaunty/main/source/Sources.gz
http://ubuntu.osuosl.org/ubuntu/dists/jaunty/restricted/source/Sources.gz
http://ubuntu.osuosl.org/ubuntu/dists/jaunty/universe/source/Sources.gz
http://ubuntu.osuosl.org/ubuntu/dists/jaunty/multiverse/source/Sources.gz

http://ubuntu.osuosl.org/ubuntu/dists/jaunty-updates/main/source/Sources.gz
```The above directories are accessed without any errors. (The observant reader may notice that the order of URL directories follows the same order of places in the '/etc/apt/mirror.list' config file.)

It is only when it tries to access the following that it fails:
```
http://ubuntu.osuosl.org/ubuntu/dists/jaunty-updates/restricted/source/Sources.gz
```The fact that the above directories and source files are correctly processed (without failure) offers a clue as to what the problem is, but the solution escapes me. Especially because I've looked, and that  URL/directory ***DOES*** contain a file named 'Sources.gz'.

In other words, there *IS* a Sources.gz file in the URL/Directory indicated, but for some reason apt-mirror is choking and saying there is NOT a Sources.gz file there.

If apt-mirror would fail when trying to access the first URL/directory, then I'd guess there's something globally wrong with the script. But for it to fail part-way through (and when the requested file clearly exists), completely baffles me.

I'm still investigating, but as I said, my own perl skills are fairly weak, and I'd sure appreciate any advice or suggestions that may be offered.

(Yes, I've thought about raising this issue in a Perl forum, but 1) I'm not sure which one would be best. And 2) I'm thoroughly confused why apt-mirror apparently works perfectly for everyone else, but craps out in a bizarre way for me.)

---

### Post by HighlyDubious on 2009-10-15
OK. I've hacked a work-around.

Let me explain what I figured out, and maybe someone down the line can either figure out a *correct* solution, or at the very least, others may be able to use this same hack if they have the same problem in the future.

I said in my previous post that the Sources.gz file exists in the URL/directory that is referenced by the error message. But at the point where apt-mirror was failing, it is no longer looking at the URL/directory for those files. As far as apt-mirror is concerned, all those 'Sources.gz' (and 'Packages.gz') files are now already copied to your local system. As a result, when it gives that error message, it's not looking at the URL, it's looking on your system for those files.

When I realized that, I followed the directory structure on my own system, and discovered that (for reasons unknown), apt-mirror had *NOT* downloaded the Sources.gz file to that referenced directory.

So, I downloaded the file manually, copied it to the place it belonged, and suddenly apt-mirror is working like a charm.

If you are getting a failure message similar to the one I got, you can try the following:

[SIZE=2]**1) Determine your 'base_path'**[/SIZE]

You will need to know where apt-mirror is storing it's files. Apt-mirror refers to that place as 'base_path'. If you will look in '/etc/apt/mirror.list', you will see that 'base_path' is set as follows by default:

```
set base_path /var/spool/apt-mirror
```

As noted in the mirror.list file, this location can be changed by the user, so if you've modified the base_path in your mirror.list file, then you will need to use that as your starting point for the following.

In my particular case, I'd modified mirror.list to say:

```
set base_path   /home/ima/apt-mirror
```

(It should also be noted that (as said in the mirror.list file), if you change the 'base_path', you must create the "mirror", "skel", and "var" sub-directories within whatever directory you define as your base_path. This step-by-step assumes you've already done that)

[SIZE=2][B]2) Using the error message, determine the correct directory path for the Source.gz (or Packages.gz) file that was not properly downloaded by apt-mirror.
[/B][/SIZE] 
In my case, the file that didn't download had the following path (substitute {base_path} for your own 'base_path')

```
{base_path}/skel/ubuntu.osuosl.org/ubuntu/dists/jaunty-updates/restricted/source/Sources.gz
```

[SIZE=2][B]3) Using your favorite browser (or ftp program), go to the related directory of your external mirror. 
[/B][/SIZE]
Once you are there, you should find the 'Sources.gz' (or 'Packages.gz') that apt-mirror failed to download.

In my case, I used firefox to go to the following URL:

```
http://ubuntu.osuosl.org/ubuntu/dists/jaunty-updates/restricted/source/
```

[SIZE=2]**4) Download the missing file to your system.**[/SIZE]

In my case, I downloaded to my own desktop. And so I now had the Sources.gz file located in:

```
/home/ima/desktop/Sources.gz
```

[SIZE=2]**5) Copy the file to the correct location.**[/SIZE]

Writing to the 'base_path' directory requires root priviledges, so you'll need to use sudo.

In my case I used the following command (substitute {base_path} for your own):

```
sudo cp /home/ima/desktop/Sources.gz {base_path}/skel/ubuntu.osuosl.org/ubuntu/dists/jaunty-updates/restricted/source/Sources.gz
```

sudo will ask you to enter your password, and then copy the file to where ever you told it.

[SIZE=2]**6) You should now be able to run apt-mirror. **[/SIZE]

If apt-mirror fails with any other missing 'Sources.gz (or 'Packages.gz') files , then you will need to repeat the above steps as many times as necessary until it can find all the necessary 'Sources.gz' (or 'Packages.gz') files. (mine worked fine after manually copying that one file)




I still don't know why apt-mirror failed to download that one file. It makes no sense to me. But at least with the above steps, I was able to hack around the problem. Unfortunately, I'm sure I'll end up having to repeat the same steps every time I want to update my local mirror.  :(

So if anyone would care to offer a better (more permanent) solution, I'm certainly open to suggestions.

---

### Post by kmcgregor on 2010-05-21
I had a similar problem. I was getting file not found errors, access denied errors, and hanging at "Proceed indexes [PPPPPPP" and such like. I think what happened was I ran the apt-mirror command as root first, and all of the files and directories under "skel" were owned by root. I chowned them to apt-mirror.apt-mirror, and now it seems to be working. At least, now it says it needs to download 19.9 GiB of stuff (and has proceeded to start downloading), so I think it's fixed.

---

