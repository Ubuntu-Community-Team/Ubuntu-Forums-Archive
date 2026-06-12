---
title: "folding @ home installation poll"
date: 2007-11-21
forum: The Cafe
---

### Post by Zelut on 2007-11-21
I'm wondering how those of you that use the Folding @ Home client install it.  If you haven't, you might be interested in my automated installer found at [http://ubuntu-tutorials.com/category/folding/](http://ubuntu-tutorials.com/category/folding/) .  I'm also interested in feedback on how to improve it for those that have been using other methods.

---

### Post by Lostincyberspace on 2007-11-21
I chose the first one but If would be better than when.

---

### Post by Flying caveman on 2007-11-21
I have FAH6.00 beta and 5.04 in my home folder, just running the beta one right now.  I guess i could load it as a session option if i wanted to.

---

### Post by Tundro Walker on 2007-11-21
I've got my MS WinXP comp at work running it as a Service non-stop.  And I squirelled it away in a folder and it stays there.

But on my Ubuntu home comp, I tossed it in a /folding folder under my home directory, but it ends up spreading itself out directly into my home directory.

EG: when it first ran, it tossed all of its files into the /folding sub-folder, so I thought it would stay there.  Then I check later, and nothing's updating (the unitinfo.txt file isn't updating).  So, I check, and it decided to move all the working/used files out into my main home folder.

What's up with that?  Is there anyway to prevent that?

Regardless of that, I start mine up as part of my Gnome session.  Even while playing FPS and such on my comp mostly, I can still crank out a project every two weeks or so.  But my WinXP comp at work, which is on all the time...it's goin gang-buster on it!

---

### Post by Zelut on 2007-11-21
@lostincyberspace - if you have problems remembering to launch it you might want to check out my folding automation script.  It will automagically launch it when the machine starts so you don't *need* to remember.  [http://ubuntu-tutorials.com/category/folding](http://ubuntu-tutorials.com/category/folding).

@Tundro Walker - another feature of my automation script is to create a dedicated system user and filesystem location to run the folding client.  This means no home folder clutter! (which is one of the primary reasons I wrote this project in the first place!)

---

### Post by D-EJ915 on 2007-11-22
I run it manually in my virtual consoles.

---

### Post by jpkotta on 2007-12-08
I'm the author of the install/init script in the [F@H wiki]("https://help.ubuntu.com/community/FoldingAtHome").  I tried out your script.  It worked well, but i couldn't see how to install the beta client, which is needed for SMP.  You should also get rid of the set name option and make it just run the client in -configonly mode, so you can set everything.  Also, there should be a mechanism to pass the client command line options, e.g. "-smp -verbosity 9".  If you did these things, I would probably just drop mine and use yours (which I see uses finstall anyway -- good to use the official unofficial Unix installer).

---

### Post by Zelut on 2007-12-08
jpkotta - it is supposed to support the SMP client.  I think I'll need to look into that.  In the majority of my deployments I need it to be completely automated so prompting for information during the installation doesn't work.  I suppose building an option that will let you customize at install is not out of the question.

The 0.5.2.1 release does not prompt for the name at installation so its completely automated.  Post installation you can run -r|--rename and update the user information.

I've spent the last week also working on a backup and restore option which can also tie into the network deployment option for mass deployment, backup and restore.

if you'd like to collaborate on some ideas for this project drop by [http://ubuntu-tutorials.com](http://ubuntu-tutorials.com) and use the contact form.  Thank you for the feedback.

---

### Post by n3tfury on 2007-12-08
> **Tundro Walker said:**
> I've got my MS WinXP comp at work running it as a Service non-stop.  And I squirelled it away in a folder and it stays there.



lol, either you have no sysadmins, or he/she's an idiot.

---

### Post by jpkotta on 2007-12-08
> **n3tfury said:**
> lol, either you have no sysadmins, or he/she's an idiot.

I did that too (ran it on my work machine, not as a service because I didn't have admin access).  They blocked completed WUs from being sent out, so I would sneakernet them back home and upload them using Wine.  <disclaimer>All of that is very bad and you shouldn't do the same.</disclaimer>  The sysadmins were pretty strict, you couldn't even install Firefox or Opera (which I did manage to install).  At my current job, I am completely in control of my computer and I run F@H just like I would at home.

---

### Post by Tundro Walker on 2007-12-08
> **n3tfury said:**
> lol, either you have no sysadmins, or he/she's an idiot.

No, actually, the admins are pretty good...better than other jobs I've had.  It's just that after working with me long enough, they realized I'm a pseudo developer / dba / power-user.   So, they gave me admin rights to my comp.

I figured that since I have to keep my comp on all the time to run scheduled tasks, it might as well be doing something beneficial in the downtime.  So, I installed the Folding@Home as a Service.

Beats running Progress Quest ad nauseum...LOL!

---

