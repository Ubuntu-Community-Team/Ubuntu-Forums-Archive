---
title: "apt-get locks up system reading package list at 99%"
date: 2011-04-23
forum: Server Platforms
---

### Post by Mojo742 on 2011-04-23
I have been playing with an annoying issue where apt-get update would lockup my server at 99% while reading the package list, requiring it to be physicality restarted. I got it fixed but figured I should write a blurb to help out people in the future (since i did not find anyone with the same problem on here) or have people explain why this was happening as I am a bit of a noob. 

Here is what was happening&#8230;

I have two DL380 servers that I am trying to get Ubuntu Server 10.10 installed on.  It took a few attempts as the installed seemed to hang on the creation of the file system.

The real issues happened after the install. This happened on 3 fresh installs, crossed two different servers (both DL380&#8217;s) and also between both 32 and 64 bit. 

When I go to do an &#8220;apt-get update&#8221; it will pull down the lists, but when it goes to read the package lists it gets stuck at 99%. If I tried to login though console, or another SSH session I could login and enter 1 command. Any command I entered that that point would lockup and that session would freeze.

So after a lot of forum searching I did not find anyone with the same issue I had (exactly) but it did give me some good ideas.  Mainly just to try and edit &#8220;/etc/apt/sources.list&#8221;
What I ended up doing was commenting out everything and then uncommenting them one by one, starting with the &#8220;main restricted&#8221; repositories and them moving onto the others.  I would then do &#8220;apt-get update&#8221; after I uncommented each one. Once I had all of the restricted repositories uncommented I did an &#8220;apt-get upgrade&#8221; followed by an &#8220;apt-get dist-upgrade&#8221; and rebooted (hopping that the updates would fix the issue). 

Finally one by one (and I can&#8217;t stress that enough that I did it 1 by 1) I uncommented in the rest of the repositories doing a &#8220;apt-get update&#8221; between each one I uncommented.

	Note: I got cocky after the first server worked and tried to uncomment all of the &#8220;universe&#8221; repositories at the same time&#8230; that was a mistake&#8230;  do not ever think you have it figured out. 

Conclusions:
I initially thought it was an issue with something dealing with the lists them self&#8217;s. I now think that the issue might have been in the sheer volume, size or something along those lines when reading the package list it had just pulled down (I just don&#8217;t know apt-get all that well so I can&#8217;t really say).  

Also aptitude had the same issues as using apt-get. 

I think the only fix to this issue is to read in the package lists one at a time, at least initially.


[SOLUTION] at least for me&#8230;
1: Comment everything in your &#8220;/etc/apt/sources.list&#8221;
2: Start by uncommenting repositories marked as &#8220;main restricted&#8221; 
3: Use &#8220;apt-get update&#8221; after you uncomment each repository
4: (might not need to do this) after all &#8220;main restricted&#8221; repositories are uncommented enter &#8220;apt-get upgrade&#8221; then do a &#8220;apt-get dist-upgrade&#8221; if you so choose. 
5: Then go back to uncommenting repositories one by one using &#8220;apt-get update&#8221; between each one you uncomment.


--UPDATE--
So the Package update works ... but now other things seem to be locking up randomly.
Just tried to edit my networking settings and I have the same issue with the system freezing. I am guessing this is a hardware issue with the server it self or something.

---

### Post by caulfiek on 2012-04-30
Hi
Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=1881365](http://ubuntuforums.org/showthread.php?t=1881365)
 
Seems he has a solution.
 
I'm getting exactly the same issue, system locks at 99%.
Actually it locks on other things too.
 
I have an older server box with an ide hard disk running 10.4 server and it's been fine so I might take the disk from that and reinstall 12.4 on my new sever box (AMD Athalon 64, 1g ram) as I 'think' this could be a hardware fault.
 
If you solve this any update would be appreciated as I really want to get my server running on 12.4 with Zentyal, as I have lots of programming projects that I want to be getting on with.
 
thx

---

### Post by caulfiek on 2012-05-01
I thought this might be a hardware issue and that was a total red herring, though I did clean and remount my cpu cooler and it's all nice and clean now.

apt-get update -o APT::Cache-Limit=25165824

This fixed it. Apparently it's a known issue.

[http://www.linuxquestions.org/questions/linux-software-2/apt-get-error-reading-packing-list-752676/](http://www.linuxquestions.org/questions/linux-software-2/apt-get-error-reading-packing-list-752676/)

Now to figure out how to set this limit permanently.

---

