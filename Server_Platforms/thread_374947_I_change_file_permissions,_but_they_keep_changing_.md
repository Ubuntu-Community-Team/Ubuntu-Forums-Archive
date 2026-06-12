---
title: "I change file permissions, but they keep changing back again!"
date: 2007-03-03
forum: Server Platforms
---

### Post by igeterrors on 2007-03-03
My apache2 server has been running great for months on Dapper.  PHP5 and MySQL5 running without a hitch -- just one big love-fest.  I've been doing some perl programming lately and I wanted to enable perl CGI scripting so I started monkeying around with my configuration and in short, not only do perl scripts not run on the server, but now I'm getting 403 Forbidden and 404 Not Found errors on ordinary html files that I could previously access just fine.  For instance, right now I'm getting:
```
Forbidden

You don't have permission to access /index.html on this server.
Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_perl/2.0.2 Perl/v5.8.7 Server at localhost Port 80
```  Well believe me, that never used to happen.  

But get this: If I look at the file permissions of /var/www/index.html in Nautilus I see that sure enough the file owner is BigDaddy (me) and the permissions are 600.  I set them to 777 and reload [http://localhost/](http://localhost/) and maybe the page loads and maybe it doesn't, but if I check the permissions again they've been changed back to 600! 

OK, I go into the terminal and go ```
sudo chmod 777 /var/www/index.html
```  That's got to do the trick, right?  But no!  I load the page in Firefox and check the permission in Nautilus again and sure enough, they're back to 600 again!  Dang!

All right, this is getting serious.  Now I go into terminal and go```
sudo chown root /var/www/index.html
```  That's got to do the trick, right?  No!  Not only are the persmissions changed back, but so is ownership!!  What the heck???  Now I know what you're thinking: just go sudo Nautilus and change the persmissions in Nautilus as root!  Well guess what?  I tried that too!  Doesn't work!  

So, I don't know what I did to mess this up and I'd give anything just to have it back to the way it was, but can anyone tell me what's going on?  I've read everything I can find and I've googled till the letters are worn off my keyboard, and anyplace I find a forum where someone has posted a problem similar to mine, I find that the question either goes unanswered or maybe one or two other people chime in with a "Yeah, I have that problem too", or someone actually offers some vague hints about "what worked for them" but the original poster never writes back so we never find out whether that was the answer or not.  Occasionally someone tells the poster that he's a moron for not being able to solve this himself, and then they all get into a big fight!  It's entertaining, but not that helpful.

At this point I am almost ready to give up, but I don't even know that that would entail.  Can I get a new config file and just copy that over the one I have?  By the way, it seems like I have about half a dozen config files for apache all in different places; is it any wonder I have no idea what to do?  Or I could just reinstall, but I'm kind of scared to do that, and I've even considered looking for some other kind of server to install instead, but then I have to worry about reconfiguring MySQL and PHP and everything else...  It's kind of like hosting at GoDaddy: it's awful, but switching to someone else might be even worse!

So please, anyone: HELP!!  I need to get this sorted out pronto.

---

### Post by kidders on 2007-03-03
Hi there,

If you're having trouble making permissions changes stick, you may be using a filesystem that doesn't support them, or perhaps overriding permissions settings with custom mount options.

Did you play with anything besides your Apache configuration while working on CGI scripting?

---

### Post by Mr. C. on 2007-03-03
Permission, users, and groups are not fickle.  The system never reverts your changes.

Test this yourself and share the output:

   # sudo -s
   # chmod 777 /var/www/index.html
   # echo $?
   # ls -l /var/www/index.html

What is the output?

MrC

---

### Post by igeterrors on 2007-03-03
> **kidders said:**
> Did you play with anything besides your Apache configuration while working on CGI scripting?
No, I didn't.> **Mr. C. said:**
> Permission, users, and groups are not fickle.  The system never reverts your changes.
I can see why you'd say that.  I would've thought the same thing!  But watch:
```
bigdaddy@bigdaddy-laptop:~$ sudo -s
Password:
root@bigdaddy-laptop:~# chmod 777 /var/www/index.html
root@bigdaddy-laptop:~# echo $?
0
root@bigdaddy-laptop:~# ls -l /var/www/index.html
-rwxrwxrwx 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html
root@bigdaddy-laptop:~#
```So far, so good.  Then I go and load the file in the browser a few times until I get the forbidden error, then go back and what do you know:```
root@bigdaddy-laptop:~# ls -l /var/www/index.html
-rw------- 1 bigdaddy bigdaddy 17249 2007-03-03 14:45 /var/www/index.html

```Not fickle?  Never reverts my changes?  Tell that to *my* system!

---

### Post by Mr. C. on 2007-03-03
I say this with 20 years working with Unix and Unix kernels.

Don't confuse what the Unix/Linux kernels do, with the problems you are experiencing.

Its clear something is happening that you don't understand.  Forget the browser, and that approach.  Lets see exactly what is happening.  Once that's solved, the rest will fall out.

1) Is the file on an NFS-mounted or remote filesystem?
2) Is the filesystem mounted read-only?
3) Is the filesystem NTFS, FAT, ext3, Reiser?
4) Is there a caching system in between?

$ mount
$ df -k /var/www/index.html
$ ls -ld /var  /var/www /var/www/*

MrC

---

### Post by scxtt on 2007-03-03
what user is apache running as (apache2.conf should tell you "cat /etc/apache2/apache2.conf | grep -i user")?

if a file (index.html) is owned by "bigdaddy" and set to "read/write" ONLY by user "bigdaddy" while apache2 is running as the apache user (pretty standard) --  then NO, browsing to those files isn't gonna work ...

if you're running apache as "bigdaddy" - that might work for you - but most browsers allow connections to your pages as "apache" or a non-machine-specific-user ...

---

### Post by igeterrors on 2007-03-03
> **Mr. C. said:**
> Its clear something is happening that you don't understand. That is nothing if not an understatement!  : )

But seriously, thanks for the help.  And thanks for not giving me commands that would wipe out my hard drive because I'm just entering whatever commands you post here!
```
bigdaddy@bigdaddy-laptop:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-686/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda4 on /media/hda4 type vfat (rw,utf8,umask=007,gid=46)

```I started out as a dual-booter, which is why you see the ntfs and vfat partitions, but I'm doing everything on hda2 which is ext3.```
bigdaddy@bigdaddy-laptop:~$ df -k /var/www/index.html
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             22374792  14404796   6833400  68% /
```The last command you gave me listed close to 100 files, but is there something in particular in that output I should be looking for?

---

### Post by gschoper on 2007-03-03
IIRC, permissions for files residing inside your web's root are going to be owned and have their umask set according to your apache config files.

HTH,

gschoper

---

### Post by igeterrors on 2007-03-03
> **scxtt said:**
> what user is apache running as (apache2.conf should tell you "cat /etc/apache2/apache2.conf | grep -i user")?

If I am reading the output correctly, apache is running as www-data.  Does this make sense?

---

### Post by scxtt on 2007-03-03
yes, that does make sense (some distros use "www-data" and some use "apache") ... so at the very least, you shouldn't make HTML files ONLY readable by a user that's not "www-data" ... think of it like there's a little user (Mr. www-data) who grabs files and sends them to your (or anyone requesting your server) browser ... "he" can't send files to a browser if he doesn't have the permission to "touch" them :)

BAD:
-rw------- 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html

OK:
-rw----r-- 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html

IDEAL:
-rw------- 1 www-data www-data 16593 2007-03-03 05:22 /var/www/index.html

---

### Post by igeterrors on 2007-03-03
> **gschoper said:**
> IIRC, permissions for files residing inside your web's root are going to be owned and have their umask set according to your apache config files.

That sounds like something I should check out.  Only I'm not sure what it means.... : )

---

### Post by scxtt on 2007-03-03
> **igeterrors said:**
> That sounds like something I should check out.  Only I'm not sure what it means.... : )apache is able to create files (via scripts) as the apache user and by default those files have specific permissions (UMASK) ... i'm not entirely sure that can be set via apache's configs, but linux on the whole has default umask settings ... doesn't really apply to your situation since you're referring to an index.html file that already exists ...

---

### Post by Mr. C. on 2007-03-03
There are several discussions going here at once; some of them are incidental and irrelevant to the problem being seen.

Umask *only* affects file and folder creation, not chmod.

The UID/GID in which apache is running has nothing to do with why the OP is seeing his permissions apparently reverting.  That is the root of the matter.

I see the FS is mounted RW, but RO on errors.  Be sure there are no errors, and you can create new files on that filesystem.

/dev/hda2 on / type ext3 (rw,errors=remount-ro)

The mount command was to be sure nothing was double mounted.

Second, the ls -ld commands were to see if there were any symlinks anway.

ls -ld /var/www/index.html
ls -ld /var/www
ls -ld /var

should be sufficient.

Next, see if you can create your own files with /var and /var/www and see if user,group,and permission behave as they should.

Also try moving index.html to index.html.old and see what occurs.

Finally, be sure you are not accessing the file via some other client, which may be reverting the permission (eg. some FTP clients can change perms, or cache their idea and uploading can revert).

Lets see what you find.

MrC

---

### Post by igeterrors on 2007-03-03
> **scxtt said:**
> yes, that does make sense (some distros use "www-data" and some use "apache") ... so at the very least, you shouldn't make HTML files ONLY readable by a user that's not "www-data" ... think of it like there's a little user (Mr. www-data) who grabs files and sends them to your (or anyone requesting your server) browser ... "he" can't send files to a browser if he doesn't have the permission to "touch" them :)

BAD:
-rw------- 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html

OK:
-rw----r-- 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html

IDEAL:
-rw------- 1 www-data www-data 16593 2007-03-03 05:22 /var/www/index.html

Thank you, that's very clear.  But you would think that this would've done the trick:

-rwxrwxrwx 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html

Only it keeps getting changed back to:

-rw------- 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html

---

### Post by scxtt on 2007-03-03
> **Mr. C. said:**
> The UID/GID in which apache is running has nothing to do with why the OP is seeing his permissions apparently reverting. That is the root of the matter.what i've been discussing has everything to do w/ why igeterrors can't view web pages through his browser ...

[QUOTE=igeterrors]Thank you, that's very clear. But you would think that this would've done the trick:

-rwxrwxrwx 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html

Only it keeps getting changed back to:

-rw------- 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html[/QUOTE]change the ownership to www-data "sudo chown www-data:www-data /var/www/index.html" (then it shouldn't matter at all) -- there's no advantage for those files being owned by you ... if that's what you want, look into **[http://localhost/~bigdaddy/](http://localhost/~bigdaddy/)** via ~/public_html (and -rw----r-- permissions) ...

---

### Post by igeterrors on 2007-03-03
> **Mr. C. said:**
> 
Finally, be sure you are not accessing the file via some other client, which may be reverting the permission

Hold the phone -- what's that again?  I *am* accessing it with another client, namely WWW-Mechanize.  But how could *it* be changing the permissions?

---

### Post by Mr. C. on 2007-03-03
> **scxtt said:**
> what i've been discussing has everything to do w/ why igeterrors can't view web pages through his browser ...

This is the *symptom*, not the *problem*.  The OP knows to change permissions and ownership, but that's where the failure occurs.

---

### Post by Mr. C. on 2007-03-03
> **igeterrors said:**
> Hold the phone -- what's that again?  I *am* accessing it with another client, namely WWW-Mechanize.  But how could *it* be changing the permissions?

No, this simply reads the file.  It is not affecting the file's INODE.  That is where permissions, GID, and UID are stored.

---

### Post by scxtt on 2007-03-03
> **Mr. C. said:**
> This is the *symptom*, not the *problem*.  The OP knows to change permissions and ownership, but that's where the failure occurs.the heart of the problem is that his method of chown'ing /var/www/index.html is NOT in line w/ how apache serves up webpages ...

not to mention doing "chmod 777 /var/www/index.html" invites ANYONE to change any aspect of the file ...

---

### Post by igeterrors on 2007-03-03
> **Mr. C. said:**
> 
ls -ld /var/www/index.html
ls -ld /var/www
ls -ld /var

should be sufficient.
Survey says:```
bigdaddy@bigdaddy-laptop:~$ ls -ld /var/www/index.html
-rw------- 1 root root 17538 2007-03-03 15:05 /var/www/index.html

bigdaddy@bigdaddy-laptop:~$ ls -ld /var/www
drwxrwxrwx 15 www-data www-data 4096 2007-03-03 15:05 /var/www

bigdaddy@bigdaddy-laptop:~$ ls -ld /var
drwxr-xr-x 15 root root 4096 2006-11-30 01:04 /var

```

---

### Post by Mr. C. on 2007-03-03
> **scxtt said:**
> the heart of the problem is that his method of chown'ing /var/www/index.html is NOT in line w/ how apache serves up webpages ...

This is nonsense.  ALL UNIX/Linux software obtains its rights from the kernel via the stat (or ALC) system call.  Period.  Apache simply attempts to open a file - the kernel either grants or denies permissions based upon the UID/EUID, GID/EGID of the process itself and the files attempted to be opened.  Chmod is THE way file permissions are changed.

> **scxtt said:**
> 
not to mention doing "chmod 777 /var/www/index.html" invites ANYONE to change any aspect of the file ...

Nobody's concerned about that right now.

---

### Post by scxtt on 2007-03-03
> **Mr. C.]This is nonsense. ALL UNIX/Linux software obtains its rights from the kernel via the (stat or ALC) system call. Period. Apache simply attempts to open a file - the kernel either grants or denies permissions based upon the UID/EUID, GID/EGID of the process itself and the files attempted to be opened. Chmod is THE way file permissions are changed.[/quote]i shouldn't even have to answer this statement ... chmodding something to 777 and then wondering why another proc can change the permissions is covered in "intro to linux" ... don't try and get all technical in an attempt to show some superiority ... i know you're smart, but don't try and step on my feet when i see something i KNOW is wrong ... the owner of /var/www/index.html and it's permissions before viewing ARE a factor, even if you don't see it now ...
[quote=Mr. C.][quote=scxtt said:**
> 
not to mention doing "chmod 777 /var/www/index.html" invites ANYONE to change any aspect of the file ...
Nobody's concerned about that right now.[/quote]as i said above, doing this (coupled w/ bigdaddy owning the file, set to R/W ONLY by bigdaddy when apache is running as www-data) is a problem ...

---

### Post by Mr. C. on 2007-03-03
> **scxtt said:**
> chmodding something to 777 and then wondering why another proc can change the permissions is covered in "intro to linux" ... 

Prove your theory.  What process exactly do you believe is changing there permissions on the index.html file, and How is it changing it.  Show the lines of code.  I'll show you a proof that I can change permission on any file I chose - apache does not change file permissions.

> **scxtt said:**
> i KNOW is wrong ... the owner of /var/www/index.html and it's permissions before viewing ARE a factor, even if you don't see it now ...
as i said above, doing this (coupled w/ bigdaddy owning the file, set to R/W ONLY by bigdaddy when apache is running as www-data) is a problem ...

Prove your theory.  Without evidence and proof, you are just huffing.

---

### Post by igeterrors on 2007-03-03
> **Mr. C. said:**
> 
Next, see if you can create your own files with /var and /var/www and see if user,group,and permission behave as they should.
I (that is, bigdaddy) can create file and folders in /var/www but not in /var
> Also try moving index.html to index.html.old and see what occurs.

```
bigdaddy@bigdaddy-laptop:~$ sudo mv /var/www/index.html /var/www/index.html.old

```
and then browse to [http://localhost/](http://localhost/) and I get```
Forbidden

You don't have permission to access /index.html.old on this server.
Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_perl/2.0.2 Perl/v5.8.7 Server at localhost Port 80
```

---

### Post by Mr. C. on 2007-03-03
> **igeterrors said:**
> I (that is, bigdaddy) can create file and folders in /var/www but not in /var

```
bigdaddy@bigdaddy-laptop:~$ sudo mv /var/www/index.html /var/www/index.html.old

```
and then browse to [http://localhost/](http://localhost/) and I get```
Forbidden

You don't have permission to access /index.html.old on this server.
Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_perl/2.0.2 Perl/v5.8.7 Server at localhost Port 80
```

Ok, this is the answer.  Apache should never have looked for index.html.old - it knows nothing about that.

Some process has the INODE for /var/www/index.html (which is now /var/www/index.html.old) open, and *this* is preventing your changes from completing.

Run the command:

ls -li /var/www/index.html.old

this will give you the inode in the left column.

Then, run:

lsof | grep INODENUM

replacing INODENUM with the inode number of the file.

What is found?

---

### Post by scxtt on 2007-03-03
> **Mr. C. said:**
> Prove your theory.  What process exactly do you believe is changing there permissions on the index.html file, and How is it changing it.  Show the lines of code.  I'll show you a proof that I can change permission on any file I chose - apache does not change file permissions.do i know exactly what process is changing the permissions AFTER igeterrors sets it to 777, NO (never said i did) -- what i am saying is that the SIMPLE fact the he sets it to 777 (even as root, and owned by root) COMPLETELY and TOTALLY invites ANY process to modify /var/www/index.html in ANY way it wants - i shouldn't have to explain that, or even state it twice ... am i saying that apache is explicitly changing permissions, no ... i am additionally stating that "-rw------- bigdaddy bigdaddy" will NOT allow browsers to view this file -- we can call that "intro to apache" ... igeterrors may have some program that is modifying permissions on his server (no one has figured that out yet) but i am saying setting the file to 777 invites the change to happen - plain and simple ...
> **Mr. C. said:**
> Prove your theory.  Without evidence and proof, you are just huffing.i'm disappointed i'd even have to explain this (to you) - and i think the "proof" is visible in this thread and could even further be shown if my "BAD / GOOD / IDEAL" settings were followed ...

---

### Post by igeterrors on 2007-03-03
Here is the whole sequence:
```
bigdaddy@bigdaddy-laptop:~$ sudo chown www-data:www-data /var/www/index.html 
bigdaddy@bigdaddy-laptop:~$ sudo chmod 777 /var/www/index.html
bigdaddy@bigdaddy-laptop:~$ ls -l /var/www/index.html
-rwxrwxrwx 1 www-data www-data 17838 2007-03-03 16:47 /var/www/index.html
```
Then I run my script:
```
bigdaddy@bigdaddy-laptop:~$ perl script_using_mechanize.pl
Uncaught exception from user code:
        Error GETing http://localhost/index.html: Forbidden at /home/bigdaddy/script_using_mechanize.pl line 108

```
Then check the file again:```

bigdaddy@bigdaddy-laptop:~$ ls -l /var/www/index.html 
-rw------- 1 bigdaddy bigdaddy 18123 2007-03-03 16:50 /var/www/index.html
```Did Mechanize change the permissions and ownership?

---

### Post by scxtt on 2007-03-03
again, setting permissions to 777 will allow anything (your script for example) to change the file in any way ...

---

### Post by igeterrors on 2007-03-03
> **scxtt said:**
> 
BAD:
-rw------- 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html

OK:
-rw----r-- 1 bigdaddy bigdaddy 16593 2007-03-03 05:22 /var/www/index.html

IDEAL:
-rw------- 1 www-data www-data 16593 2007-03-03 05:22 /var/www/index.html

The problem with using your IDEAL setting is that my perl script must be able to edit the file before mechanize browses to it.  Is there another setting and/or do I need to/is there a way to make my perl script a user???  Or run it as root?

---

### Post by scxtt on 2007-03-03
well we now know why the permissions change - i have no idea what mechanize is supposed to do or how to trouble shoot it, but it is the reason for your permission trouble ...

you'd need to visit a "mechanize" group, read the man page on it (if there is one) or follow something specific to it ...

---

### Post by Mr. C. on 2007-03-03
> **igeterrors said:**
> Here is the whole sequence:
```
bigdaddy@bigdaddy-laptop:~$ sudo chown www-data:www-data /var/www/index.html 
bigdaddy@bigdaddy-laptop:~$ sudo chmod 777 /var/www/index.html
bigdaddy@bigdaddy-laptop:~$ ls -l /var/www/index.html
-rwxrwxrwx 1 www-data www-data 17838 2007-03-03 16:47 /var/www/index.html
```

Excellent.  You've demonstrated the "system" didn't change permission on its own.
> **igeterrors said:**
> 
Then I run my script:
```
bigdaddy@bigdaddy-laptop:~$ perl script_using_mechanize.pl
Uncaught exception from user code:
        Error GETing http://localhost/index.html: Forbidden at /home/bigdaddy/script_using_mechanize.pl line 108

```

I (incorrectly) assumed the mechanize.pl script was being run on the browsing station.

It, or your use if it, is responsible for keeping the file's inode open, or reverting the permissions (I look at the mechanize code briefly).  Again, you can easily verify this if your mechanize program runs and continues running, via another terminal, look for that inode in the lsof output. If the inode's open, you'll find it.

> **igeterrors said:**
> 
Then check the file again:```

bigdaddy@bigdaddy-laptop:~$ ls -l /var/www/index.html 
-rw------- 1 bigdaddy bigdaddy 18123 2007-03-03 16:50 /var/www/index.html
```Did Mechanize change the permissions and ownership?

To me, this is case closed.  Your script has changed your index.html file.

Now as to permissions / ownership, what is it that you want to accomplish?

MrC

---

### Post by igeterrors on 2007-03-03
> **scxtt said:**
> well we now know why the permissions change> **Mr. C. said:**
> To me, this is case closed.  Your script has changed your index.html file.
I agree with both your assessments. Thank you for helping me get this far.
> **Mr. C. said:**
> Now as to permissions / ownership, what is it that you want to accomplish?
I want the script to be able to read and write to the file and then browse to/interact with it while leaving the permissions the way they are so that it can read, write and browse to the file repeatedly.

---

### Post by igeterrors on 2007-03-03
> **Mr. C. said:**
> It, or your use if it, is responsible for keeping the file's inode open, or reverting the permissions (I look at the mechanize code briefly).  Again, you can easily verify this if your mechanize program runs and continues running, via another terminal, look for that inode in the lsof output. If the inode's open, you'll find it.
I'm afraid this went over my head...

---

### Post by Mr. C. on 2007-03-03
Close down your script.

Create a new user for the mechanize script, say "mech".

Change the ownership of the file to "mech", group "www-data" (or whatever group apache is running under for your system).

Set the permissions to 644 or 640.

Run your mech script setuid "mech".

Be sure in your script that you call their Get operation each time a page changes.  One your permissions are set, THEN run your script.  Only the "mech" script can then change the file (or its permissions!) and apache can read.

MrC

---

### Post by Mr. C. on 2007-03-03
> **igeterrors said:**
> I'm afraid this went over my head...

Sure, no problem.

Here a quick way for you to understand what I'm describing.

Run the following:

  cat > goober

and then hit Control-Z to stop the process.

Now run:

  ls -i goober

You will get a number in the left column.  That's the "inode number".

Now, run:

  lsof | grep THATNUMBER

replacing THATNUMBER with the number you saw in the left column.

as is:

$  ls -i goober
1046749 goober
$  lsof | grep 1046749
cat       13377       root    1w      REG        3,6       0    1046749 /home/mrc/goober

This tells me the "cat" process (left column of output) has file "goober" open.

Now you can do the same with your script and index.html to see what process has the file open.  This will give you a hint about which process is mucking with the file behind your back, like removing it, and replacing it with the same-named file.  You can verify this too, by checking the inode number before and after each time your run your script. Changed inode = old file deleted, and new file created with the same name.

The reason the answer was clear after seeing the data is because of how files are open.  Apache could not have known the name of index.html.old; therefore, something else must have given that name to apache to open.

Anyway, you have your answers now.  Enjoy.

MrC

---

### Post by igeterrors on 2007-03-03
> **Mr. C. said:**
> Close down your script.Done.
> **Mr. C. said:**
> Create a new user for the mechanize script, say "mech".Done.  (Did you, by the way, mean that I should create the user mech in the group www-data?  Because that is what I did.)> **Mr. C. said:**
> Change the ownership of the file to "mech", group "www-data" (or whatever group apache is running under for your system).Done.> **Mr. C. said:**
> Set the permissions to 644 or 640.Done (640).> **Mr. C. said:**
> Run your mech script setuid "mech".This is where you lost me.  Could you please elaborate?

---

### Post by igeterrors on 2007-03-03
> **Mr. C. said:**
> The reason the answer was clear after seeing the data is because of how files are open.  Apache could not have known the name of index.html.old; therefore, something else must have given that name to apache to open.
In all the excitement I somehow missed [_post #25_]("http://ubuntuforums.org/showpost.php?p=2243294&postcount=25") where you addressed that.  By the way, thank you for spending all this time helping me.  I really appreciate it.

---

### Post by Mr. C. on 2007-03-03
> **igeterrors said:**
> Done.
Done.  (Did you, by the way, mean that I should create the user mech in the group www-data?  Because that is what I did.)Done.Done (640).This is where you lost me.  Could you please elaborate?

No, I meant in /etc/passwd.  You create a new user named "mech", and give the user a new UID / GID, and no shell.

Then you run:

  chmod 4755 yourscript

This runs the script as user "mech", no matter who runs the script.  There are security implications in this, but for now, don't worry about those.

MrC

---

### Post by igeterrors on 2007-03-03
> **Mr. C. said:**
> No, I meant in /etc/passwd.  You create a new user named "mech", and give the user a new UID / GID, and no shell.
OK, so user "mech" is now a member of group "mech"

> **Mr. C. said:**
> Then you run:

  chmod 4755 yourscript

This runs the script as user "mech", no matter who runs the script.

Sorry to be so dense, but how does it do that?  In other words, what part of "4755" refers to the user "mech"?

---

### Post by igeterrors on 2007-03-03
> **Mr. C. said:**
> 
Change the ownership of the file to "mech", group "www-data" (or whatever group apache is running under for your system).

Set the permissions to 644 or 640.



Uh-oh...  I thought "the file" you referred to above was "index.html" so that's the file on which I performed the actions described above.... but now I'm thinking maybe it was "mechanize.pl" you were talking about....?!??!

---

### Post by Mr. C. on 2007-03-03
Let see if I can clarify, and make this simpler.  Once you have the basics, we can make it more secure.

Forget user "mech" for the time being.  Instead, we're going to have you own the files.

chown bigdaddy:www-data index.html

and

chmod 644 index.html

and do likewise to any other files your script will change.  This changes you to own the file, and www-data to be group on the file.

Now, your mech script:

  chown bigdaddy:bigdaddy mechanize.pl

This gives you ownership and group ownership of your script.

  chmod 4755 mechanize.pl

This changes the file permissions to rwxr_xr_x but adds an additional bit (4000 bit) that forces the program mechanize.pl to run as bigdaddy no matter who runs the program.  This, the mechanize.pl can *always* write to index.html provided the permission were set as above.

I've been assuming that your script is invoked via a CGI or something else.  This is why we set it "setuid" (man chmod for more info), so that it always runs as YOU, no matter how it starts.  If you are always the person running the script, you don't need setuid.  But if some other program or service will start the script, it is usually consider more secure to create a unique user (in /etc/passwd) that cannot login (no shell), and that user will own index.html and mechanize.pl.  The setuid program will then ran as that user, which of course can modify the index.html file.  Again, this is moot if you are the person always running the script.

Make sense?
MrC

---

### Post by igeterrors on 2007-03-03
Let me just thank you again for all your attention and help, without which I would never have found the source of this problem.  

It turns out it's not the Mechanize.pm module that is at fault but the Inplace.pm module, which is the module that does the editing of the file before Mechanize gets to it.  If I chmod the file and then just send Mechanize to browse it, without Inplace.pm modifying it first, there's no problem.  

The solution:  add two meager lines of code to the perl script chmoding the file back to 755 before Mechanize browses to it!   :guitar: 

And to think I was almost going to reinstall Apache!  I guess the fact that I first noticed the problem after I'd been monkeying around with my Apache config was just, dare I say it, *a coincidence???*

I mean, perl CGI still isn't happening, but at least the script is working.

Seriously, thank you, MrC.  This is probably the most intensive help/tutorial I've ever received on a message board.  I really appreciate you sticking with me all the way through!

And scxtt, you were extremely helpful too.  It was your insistence that setting the file to 777 allowed anyone or anything, even my perl script, to change any aspect of the file, even its ownership/permissions, that got me headed down the right track.

So my warmest thanks to you both!

---

### Post by Mr. C. on 2007-03-04
You're welcome.  As to intensive help sessions, you'd love my courses ! :-)

Your files are getting created 600 because your default umask for your shell is set to 077, which 0's out group-other permission upon file creation.  Change your umask in your perl program, and all files will be created with according permissions:

$ umask 
0077
$ touch bb
$ ls -l bb
-rw------- 1 mrc users 0 Mar  3 21:13 bb
$ umask 000
$ touch cc
$ ls -l cc
-rw-rw-rw- 1 mrc users 0 Mar  3 21:13 cc

Files / directories will be created with all permissions set, by default.  It is your umask setting that blocks some.

Call the perl umask function.  For a good explanation, man perfunc and search for the umask description.

Read my lecture notes: [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/) for week 2 (Files, Directories, Permissions and Ownership) for an explantion of how this works.

Best of luck,
MrC

---

