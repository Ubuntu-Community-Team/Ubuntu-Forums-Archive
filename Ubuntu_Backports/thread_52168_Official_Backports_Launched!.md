---
title: "Official Backports Launched!"
date: 2005-07-26
forum: Ubuntu Backports
---

### Post by Mez on 2005-07-26
The Official Backports project has now officially been launched

To add the Official repositories to your /etc/apt/sources.list, add the following line

```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```

And this will add the official repositories to your list.

You may, if you want remove the old backports repositories from your list, and this won't cause any harm.

Please note that hoary-extras will stay on the old repositories, this will NOT be made official

To report a bug: go here: [https://launchpad.ubuntu.com/projects/ubp/ubp-hoary/+filebug](https://launchpad.ubuntu.com/projects/ubp/ubp-hoary/+filebug)

Our Mailing list is here: [http://lists.ubuntu.com/mailman/listinfo/ubuntu-backports](http://lists.ubuntu.com/mailman/listinfo/ubuntu-backports)

Please, feel free to join the mailing list, or start reporting bugs!

This is a great step forward for us, and I'm sure everyone's agreed that it's good we've made it.

---

### Post by stoffe on 2005-07-26
How about staging, can (or should) that be removed or moved?

Otherwise, good news! :)

---

### Post by cafuego on 2005-07-26
[QUOTE=Mez]

To add the Official repositories to your /ets/apt/sources.list, add the following line

Typo, you probably mean /etc/apt/sources.list  ;-)

---

### Post by Mez on 2005-07-26
[QUOTE=cafuego][QUOTE=Mez]

To add the Official repositories to your /ets/apt/sources.list, add the following line

Typo, you probably mean /etc/apt/sources.list  ;-)[/QUOTE]
 yeah, I did, thanks!

I'll fix that

Staging can be removed if you want, it's up to you... We haven't discusssed what we're going to keep on the old servers yet.

---

### Post by rwabel on 2005-07-26
I had so far these 3 in my sources.list.
deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-backports-staging main universe multiverse restricted

deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-backports main universe multiverse restricted

deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-extras main universe multiverse restricted

Is it the second one, which I can replace with the official one?

thanks

---

### Post by jiyuu0 on 2005-07-26
Will the mirrormax still be supported?

Is everything there in the official repo?

---

### Post by AndyAWS on 2005-07-26
After changing the Backports server (I kept mirrormax extras and both staging repos) I now have a couple dozen packages showing up as local/obsolete...abiword, amarok, firefox, and totem, to name a few.

I'm guessing things are still being bumped around a bit.

Personally I'm not making any other changes/upgrades until things settle out.
 ;-)

---

### Post by bored2k on 2005-07-26
Very nice.

---

### Post by strikeforce on 2005-07-26
[QUOTE=jiyuu0]Will the mirrormax still be supported?

Is everything there in the official repo?[/QUOTE]

I'm in the same boat.  If everything is supported I'll switch I mean I might be forced to switch however I'm hoping everything is still the same and its just switched to a different server :P

---

### Post by bored2k on 2005-07-26
Adding the new line presented me with 13 new updates (from ubp to hoary - one of them being Clearlooks .6). Are they safe?

---

### Post by Brian Puccio on 2005-07-27
[QUOTE=rwabel]I had so far these 3 in my sources.list.
deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-backports-staging main universe multiverse restricted

deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-backports main universe multiverse restricted

deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-extras main universe multiverse restricted

Is it the second one, which I can replace with the official one?

thanks[/QUOTE]

Yes, the second one can be replaced.

I think it needs to be noted that the extras portion of the backports will NOT be on the ubuntu servers. I believe those will still need to be supported by and hosted by the community (read: not canonical) due to legal reasons.

---

### Post by rwabel on 2005-07-27
[QUOTE=Brian Puccio]Yes, the second one can be replaced.

I think it needs to be noted that the extras portion of the backports will NOT be on the ubuntu servers. I believe those will still need to be supported by and hosted by the community (read: not canonical) due to legal reasons.[/QUOTE]
 thanks, then I'm settled :-)

---

### Post by man.life on 2005-07-27
There is a lot of backports which haven't been moved to the official backports repository: firefox, f-spot, abiword, blam, mono...

---

### Post by JaM on 2005-07-27
[QUOTE=man.life]There is a lot of backports which haven't been moved to the official backports repository: firefox, f-spot, abiword, blam, mono...[/QUOTE]
 If you use the official backports, will it cause troubles when upgrading to breezy?

---

### Post by Mez on 2005-07-27
no, official backports will not cause problems.

Any upgrades tha you may get are completely safe (maybe even safer)

And not everything has moved yet, but will move.

If you could send me links regarding the packages that haven't moved, I can get them built.

---

### Post by rwabel on 2005-07-27
[QUOTE=Mez]no, official backports will not cause problems.

Any upgrades tha you may get are completely safe (maybe even safer)

And not everything has moved yet, but will move.

If you could send me links regarding the packages that haven't moved, I can get them built.[/QUOTE]
 that means only with the new bp, which got accepted, you won't get in trouble. But it could be with the others, right?

---

### Post by Velvet Elvis on 2005-07-27
So are file names changing with the move, droping the "ubp" from the version info or are these new backports that are showing up?

I'm stuck on dialup and would rather not upgrade the gimp and acroread just to change the name.

---

### Post by Omnios on 2005-07-27
WOOP Great work! If it wasn't for comming accross this post yesterday I wouln't have known of it. And got lots up updates this morn.

---

### Post by DancingSun on 2005-07-28
When can we expect the AMD64 backports be available?

---

### Post by AndyAWS on 2005-07-28
Is there anything we can do to fix the missing packages?
I know it's only an annoyance but I don't like having so many listed as (local or obsolete).
Will re-adding the old backports repo (mirrormax) do the trick, or will that cause other problems?

---

### Post by AndyAWS on 2005-07-28
[QUOTE=Mez]
And not everything has moved yet, but will move.

If you could send me links regarding the packages that haven't moved, I can get them built.[/QUOTE]


Ok, somehow I missed this, disregard my last post...waiting patiently   :-| 

I don't think I can help you with the links but I can give you a list of what packages show up as missing in Synaptic on my system, if that will help.

---

### Post by ShaneAu on 2005-07-29
[QUOTE=AndyAWS]Ok, somehow I missed this, disregard my last post...waiting patiently   :-| 

I don't think I can help you with the links but I can give you a list of what packages show up as missing in Synaptic on my system, if that will help.[/QUOTE]
 You don't have to move over just yet, why the rush? I think the old mirrors are still being updated with new stuff. (I think)

---

### Post by AndyAWS on 2005-07-30
You're right, there are updates on the Mirrormax backports repo that aren't in the 'Official' one yet.
I guess there's no harm in having both for now, as the packages in the new repo have been renamed and take precidence over the old ones.

---

### Post by jcohen on 2005-08-01
It's only listed as local/obsolete because you removed the old Backports repository and those packages are not available in the new Official Backports repository. This is nothing to worry about. These packages will soon be made available in the Official Backports repository.

---

### Post by ghostintheshell on 2005-08-02
great work, thank you!

I replaced:

 ```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
``` 

by:

 ```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
``` 

and after an update, some files were updated (clearlooks, gimp, xchat, fileroller, easytag, doxygen).

you rulez men.

---

### Post by AndyAWS on 2005-08-03
[QUOTE=jcohen]It's only listed as local/obsolete because you removed the old Backports repository and those packages are not available in the new Official Backports repository. This is nothing to worry about. These packages will soon be made available in the Official Backports repository.[/QUOTE]


Yes, I knew that...I was just letting someone know that they were not there yet, in case it was an oversight. The solution is just to have both the old and new repos in your sources list for now, until everything is transferred over, or to just ignore the missing packages until they show up.

---

### Post by Mez on 2005-08-04
Please foward any requests for things that arent in official backports to [email]ubuntu-backports@lists.ubuntu.com[/email]

---

### Post by samjam on 2005-08-20
[QUOTE=Mez]The Official Backports project has now officially been launched

To add the Official repositories to your /etc/apt/sources.list, add the following line

```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```
[/QUOTE]

Backports are much appreciated.

While the deb-src to the backports be enabled?
I'm an open source hackery type of guy and lack of back-ports source is becoming awkward for me, I have some package conflicts I could fix if I had backports source (deb-src).

Sam

---

### Post by AndyAWS on 2005-08-20
I believe the Backports are built from Breezy sources, which are in the Breezy src repos.

---

### Post by allanux on 2005-08-22
when i try to execute the command apt-get update at the end of the message I recieved an error message :

gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
  Sub-process gzip returned an error code (1)
Fetched 84.8kB in 4m37s (306B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

any familiar with these?

---

### Post by AgenT on 2005-08-22
Retry. Maybe your connection to the server was interrupted.

---

### Post by evilmrt on 2005-08-23
Had the same problem. Ran the command in the terminal (didn't save it..how?). It works now! Thanks!  \\:D/

---

### Post by vrln on 2005-09-19
Great to see backports as an official Ubuntu project. Just one question though: when will you start supporting Breezy?

---

### Post by matthew on 2005-09-19
[QUOTE=vrln]Great to see backports as an official Ubuntu project. Just one question though: when will you start supporting Breezy?[/QUOTE]
After the development of Breezy is complete and it is realeased and development has begun on the next release of Ubuntu called Dapper Drake.

---

### Post by DancingSun on 2005-09-19
[QUOTE=vrln]Great to see backports as an official Ubuntu project. Just one question though: when will you start supporting Breezy?[/QUOTE]
The backports project ports packages that are in the current Ubuntu in development.  Right now, that means the project port packages that are included in Breezy Development.  So if you are concerned that these nice packages in the backports will not be available in the Breezy release, don't worry, these are already in Breezy.

---

### Post by DrakeGuan on 2005-09-20
[QUOTE=DancingSun]The backports project ports packages that are in the current Ubuntu in development.  Right now, that means the project port packages that are included in Breezy Development.  So if you are concerned that these nice packages in the backports will not be available in the Breezy release, don't worry, these are already in Breezy.[/QUOTE]
 Then, how about "ubuntu-backports.mirrormax.net" now? it seems this machine was done for a while?!

---

### Post by Vicsun on 2005-09-21
*w32codecs* and *sun-j2re1.5* packages seem to be missing from both the new official backports and the old mirrormax ones. What gives?

edit: the problem [isn't isolated to me](http://www.ubuntuforums.org/showthread.php?t=66843&page=1&pp=10&highlight=%2Aj2re%2A)

---

### Post by seiflotfy on 2005-09-22
for some reason i still have them ionstalled

---

### Post by idn on 2005-09-22
[QUOTE=Vicsun]*w32codecs* and *sun-j2re1.5* packages seem to be missing from both the new official backports and the old mirrormax ones. What gives?

edit: the problem [isn't isolated to me](http://www.ubuntuforums.org/showthread.php?t=66843&page=1&pp=10&highlight=%2Aj2re%2A)[/QUOTE]

where can I find theses prackages? I only really want to use the offial repos

---

### Post by Rory on 2005-09-29
I have two basic questions:

1) Before, I was told to add "bleeding" to my backports repo line.  Now it doesn't work.  What is/was bleeding and is it now dead?

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted bleeding

2) What is "Staging" and should I add it?

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports-staging main universe multiverse restricted


Thanks for your help.

Rory

---

### Post by Wide on 2005-09-30
The Ubuntu staff does a great job of moving in the right direction.

Very good read here, I had update issues then found this, I'll wait untill the smoke clears unless it's a security breach for my system.


:)

---

### Post by dcstar on 2005-10-01
[QUOTE=Mez]The Official Backports project has now officially been launched
To add the Official repositories to your /etc/apt/sources.list, add the following line
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```
And this will add the official repositories to your list.
You may, if you want remove the old backports repositories from your list, and this won't cause any harm.
Please note that hoary-extras will stay on the old repositories, this will NOT be made official
.........[/QUOTE]
Can someone please PLEASE update things like this (and the other "FAQ"s) with this new information:
[http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)
All these existing sources of information still seem to have the wrong data in them, very confusing for anyone trying to use the Backports.

---

### Post by essexman on 2005-10-01
[quote=dcstar]Can someone please PLEASE update things like this (and the other "FAQ"s) with this new information:
[http://ubuntuforums.org/showthread.php?t=40291]("http://ubuntuforums.org/showthread.php?t=40291")
All these existing sources of information still seem to have the wrong data in them, very confusing for anyone trying to use the Backports.[/quote]

I'm glad I found this thread, how does this get updated in the ubuntuguide?  I think this would help folk.

---

### Post by essexman on 2005-10-01
[quote=essexman]I'm glad I found this thread, how does this get updated in the ubuntuguide? I think this would help folk.[/quote] And now firefox is working again, I can inset code and smilies:smile::razz:;-)

---

### Post by John.Michael.Kane on 2005-10-01
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse <---- came from this post [http://ubuntuforums.org/showthread.php?t=69681](http://ubuntuforums.org/showthread.php?t=69681)

Are these both the same. cause when i list them both it get errors..

---

### Post by jdong on 2005-10-01
They are indeed the same, just components have been listed in different orders (which APT ignores anyway)

---

### Post by bugi on 2005-10-04
I have this error while updating backport repo

```
http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz: MD5Sum mismatch
http://archive.ubuntu.com/ubuntu/dists/hoary-updates/universe/binary-i386/Packages.gz: MD5Sum mismatch
```

Whats wrong with it?

---

### Post by Sionide on 2005-10-27
I'm still confused by whether it's alright or not, to use the Hoary backports under Breezy?

---

### Post by mpettitt on 2005-10-27
Shouldn't need to, given that all the hoary-backports were from things that were in the breezy development tree, and hence should be in breezy without needing backports...
If something is missing, though, it would probably be worth asking here about the particular package before trying.

---

### Post by Sionide on 2005-10-27
Ah I see

---

### Post by tomski on 2005-11-02
so to confuse things further,
seeing as the hoary-backports were 'from things that were in the breezy development tree'... i should be able to use the brezzy-backports in hoary then yeah
or have i just lost the plot and ran off the edge of the roof!!!

---

