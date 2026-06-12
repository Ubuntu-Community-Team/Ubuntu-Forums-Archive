---
title: "Local MoinMoin wiki?"
date: 2006-07-13
forum: The Cafe
---

### Post by hizaguchi on 2006-07-13
Ok, I'm cooping in an engineering group and we just got some new software.  The responsibility to learn it, implement it, and then train everybody else has fallen on me.  Since my employment is temporary, I've written a help/HowTo file to leave behind so I don't get phone calls for tech support a few months down the road.

My original idea was to put the help into a small web site that I could just stick on one of the shared drives and give everybody a link to.  This way it is more organized than just a big, long text file and I can plant pictures in it and make sure everybody sees them the same way.  Then it occured to me that once I'm gone, nobody that's left will be able to edit the HTML. ](*,) 

So I thought, "Ah ha!  I'll make a Wiki!"  Followed shortly thereafter by, "Ah crap!  I have no idea how to make a Wiki!"

I'm looking into MoinMoin and I'm lost and confused.  If I don't want to host this thing on the internet, just on a local shared drive, should I just use the "Desktop Edition"?  Once it's set up, are people going to be able to make changes to it if something I write changes or turns out to be wrong?  How about adding pages?  How about if they decide to stick it on a web server later on?  Should I use the non-desktop edition just in case?  Even if it's only going to be used occasionally?

Ideally, I'd like to set it up something like the Ubuntu wiki, so that everybody using the software can read it and edit it if necessary, without much effort and without installing additional software on each machine.  Am I barking up the right tree?

---

### Post by az on 2006-07-13
Maybe you want a wiki, maybe you want a CMS?

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

Drupal is a Content Management System with a wiki plugin, AFAIK.  You can use Drupal for a lot of things.

---

### Post by hizaguchi on 2006-07-13
Ah, I had never heard of that before.  Drupal may not be what I need since these are all Windows computers. :(  I'm looking on their site for a Windows version though.  Or I may find another content management system.

In the mean time, I've been checking out the MoinMoin desktop edition, and it looks promising.  But, does anybody know if I need to use a web server to share it with people on my local network?  I'm kinda dumb when it comes to pretty much anything networkish.  I can see the site by browsing to 127.0.0.1:8080 on the computer that's running Moin, but I don't know how to see it from other computers.  I tried putting in the computer's IP address (even after opening port 8080 in the Windows firewall controller) and no luck.  Is that because the other computers are looking for that IP address on the internet instead of the LAN?  Or is it because I'm doing something totally wrong? :)

---

### Post by az on 2006-07-13
> **hizaguchi said:**
> Ah, I had never heard of that before.  Drupal may not be what I need since these are all Windows computers. :(  I'm looking on their site for a Windows version though.  Or I may find another content management system.

It's a web application like moin moin.  It runs on the server and you see it in your web browser, regardless of what Platform or browser you are using.  

Anyone can use it, even someone in from of a windows box.

> **hizaguchi said:**
> 
In the mean time, I've been checking out the MoinMoin desktop edition, and it looks promising.  But, does anybody know if I need to use a web server to share it with people on my local network?  I'm kinda dumb when it comes to pretty much anything networkish.  I can see the site by browsing to 127.0.0.1:8080 on the computer that's running Moin, but I don't know how to see it from other computers.  I tried putting in the computer's IP address (even after opening port 8080 in the Windows firewall controller) and no luck.  Is that because the other computers are looking for that IP address on the internet instead of the LAN?  Or is it because I'm doing something totally wrong? :)


I really don't know what the Desktop edition is.  You should be able to access one box on your lan from all the other boxes on the same LAN.

---

### Post by az on 2006-07-13
Okay, I just looked up the Desktop Moin Moin edition.  I beleive the only difference between this and the regular version is that it does not serve pages to anybody but the localhost.

I think you just need the regular version.  It seems to be (I may be wrong) that the Desktop version is just a demo.

---

### Post by hizaguchi on 2006-07-13
Thanks. :)

I understand the web interface to Drupal being OS independent, but don't you need a Unix-ish server to run it on?  The only non-Microsoft computer in the building is my laptop.  Our departement's server is Windows 2003.  To be honest though, I havn't had a chance to read any more on Drupal because alot of other work kinda swamped me.  I'll be checking into it though.

You're probably right about the Moin "desktop edition" being mainly for trial purposes.  That was my first impression too, but I started thinking otherwise when I read that it is for individuals or a small workgroup.  Maybe they meant that the small workgroup is all using the same computer. :)

I'll do some more reading tonight and give it another shot in the morning.

---

### Post by ubuntu_demon on 2006-07-13
Here's a specification for a more easy to use Wiki which might make Edgy :
[https://wiki.ubuntu.com/WikiForEft](https://wiki.ubuntu.com/WikiForEft)

The idea is to (initially) use MoinMoin (I think the desktop version) and make it so easy that everyone can set it up and use it (and some nice templates might be provided).

---

### Post by WildTangent on 2006-07-13
> **azz said:**
> Okay, I just looked up the Desktop Moin Moin edition.  I beleive the only difference between this and the regular version is that it does not serve pages to anybody but the localhost.

I think you just need the regular version.  It seems to be (I may be wrong) that the Desktop version is just a demo.

It probably wouldn't be too hard to edit it so that it will serve to other computers on the network.

-Wild

---

### Post by az on 2006-07-13
> **WildTangent said:**
> It probably wouldn't be too hard to edit it so that it will serve to other computers on the network.

-Wild

Doesn't the original version already do that with apache?

hizaguchi:  You can run apache, php and mysql on windows....

---

### Post by WildTangent on 2006-07-13
> **azz said:**
> Doesn't the original version already do that with apache?

hizaguchi:  You can run apache, php and mysql on windows....

It would be more convenient with the desktop edition as I would assume its running its own built in webserver, so there's not need to install Apache, and waste countless hours configuring PHP and MySQL on Windows. Trust me, it's not fun.

-Wild

---

### Post by hizaguchi on 2006-07-13
Yeah, I was hoping for the built-in server to work for what I'm doing.  I really don't want to get into installing a bunch of services that'll need to be maintained by somebody after I'm gone, just for a fancy help file.  I'm not really sure why it can't be done without even changing MoinMoin anyway.  It's serving the wiki to port 8080, and since I'm using the computer it's running on I can see the wiki.  All I need now is for other computers to be able to see port 8080 on that computer, right?  Doesn't seem like it would need a full-blown web server for that.  But like I said, I have no idea when it comes to this stuff.  I appreciate all the help though.  Very much!

---

### Post by WildTangent on 2006-07-13
> **hizaguchi said:**
> Yeah, I was hoping for the built-in server to work for what I'm doing.  I really don't want to get into installing a bunch of services that'll need to be maintained by somebody after I'm gone, just for a fancy help file.  I'm not really sure why it can't be done without even changing MoinMoin anyway.  It's serving the wiki to port 8080, and since I'm using the computer it's running on I can see the wiki.  All I need now is for other computers to be able to see port 8080 on that computer, right?  Doesn't seem like it would need a full-blown web server for that.  But like I said, I have no idea when it comes to this stuff.  I appreciate all the help though.  Very much!

Nah, it must be setup to only accept traffic from localhost. The setting for that must be in a config file somewhere. Try emailing the moinmoin devs and see if they can help you.

-Wild

---

### Post by hizaguchi on 2006-07-14
Alrighty, I'll check with them.  The config file is like 4 lines long though, so unless there are more of them somewhere I kinda worry that it's built to work that way.  Thanks for all your help guys.

---

### Post by hizaguchi on 2006-07-14
Ah ha, ghetto solution.  I just installed the desktop edition of MoinMoin to the shared folder and now everybody can run the built in server for their own machine and see the pages at their own localhost.  But all the files are stored in that central shared folder so changes apply to everybody.  Not a perfect solution, but if I make a shortcut to the front page that launches the wiki server in the background, I don't think anybody will notice.

Edit: Even better solution.  There is a config file missing from the desktop edition.  The magic of copy and paste allows it to host the wiki to other computers.  Works at least on the local network, dunno about further.

---

### Post by hizaguchi on 2006-07-14
Woohoo.  It's on the server, it serves pages to everybody on the local network, and I finally got the access control list set up right.  Which taught me one very important lesson: Notepad is a steaming pile of crap.  It took me half an hour to get the access controls right, and finally I emailed it to myself, opened it on my laptop, cleaned up Notepad's formatting crap, sent it back, and it worked.

---

### Post by rowanparker on 2006-07-14
Glad you got it sorted.

Although just for future reference you should try [XAMPP]("http://www.apachefriends.org/en/xampp.html"). It's **W**indows **A**pache **M**ySQL **P**HP/**P**erl. You don't need much configuring at all.

---

### Post by odin1965 on 2007-05-16
I, too, am trying to do exactly the same thing as you did. Could you tell me what exactly was missing and how you got it to work?

> **hizaguchi said:**
> Woohoo.  It's on the server, it serves pages to everybody on the local network, and I finally got the access control list set up right.  Which taught me one very important lesson: Notepad is a steaming pile of crap.  It took me half an hour to get the access controls right, and finally I emailed it to myself, opened it on my laptop, cleaned up Notepad's formatting crap, sent it back, and it worked.

---

### Post by odin1965 on 2007-05-16
OKAY, I am now able to access it from the entire network.

You have to edit the moin.py file and change the interface='localhost' to interface=' '

---

### Post by nomnex on 2010-05-23
What's the current file name and location? I want to do the same.

---

### Post by cariboo on 2010-05-23
This is a three year old thread. If you need help with moinmoin,
start a thread in the sever platforms sub-forum. This thread is closed.

---

