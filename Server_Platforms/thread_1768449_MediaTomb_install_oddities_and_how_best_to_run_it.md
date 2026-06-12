---
title: "MediaTomb install oddities and how best to run it?"
date: 2011-05-26
forum: Server Platforms
---

### Post by GROwen on 2011-05-26
Hi all,

I'm having a few troubles getting MediaTomb running under Ubuntu 11.04 and in my attempts to fix it have put myself in a tangle.

After an initial installation of MediaTomb I clicked on the MediaTomb icon that had been placed in the launcher which gave me a 'UI disabled: see your config file' error (even after making sure UI was set to 'yes' in the config file).
      
I unistalled MediaTomb, made sure I had all the dependencies installed (done through synaptic) and reinstalled MediaTomb through the Software Centre.

I tried to open MediaTomb using the icon (which was not placed in the launcher on this install) that was in my dash. Doing that gave me the error;

"can't find /var/lib/mediatomb/mediatomb.html"

I then ran mediatomb from terminal and attempted to open using the icon instead of copying and pasting the link from terminal...same error.

I then copied and pasted the address into a browser, things were looking up, I saw the UI and added media to the database, so easy.

I was able to find Mediatomb using a UPnP client on the network but could not see any of the directories

I thought this may have meant that MediaTomb had stopped running 

I thought I'd try stopping the service by running /etc/init.d/mediatomb stop

But was told the service was not running

I then tried starting the service by running /etc/init.d/mediatomb start which failed.

so I ran mediatomb from console again which gave me a new address.

I opened this in a new browser and found that the media I had added wasn't on the database view. I then realised that I'd started a new server.

Going back to the initial address I confirmed that media had been added to the original database. I checked the UPnP client again, which could see the server but none of the directories.

I thought I tried a restart of the PC that was running the server but on entering the previous addresses asked me for a username and password, using the default one I could find in config.xml didn't do anything.

I've now acccepted I have no idea wtf is going on. and need to learn more about setting it up and how to correctly run it.

I've uninstalled MediaTomb again, run remove --purge mediatomb and deleted every file I could find that had the word mediatomb in it and am going to start from scratch.

Before I do I wanted to make sure I'm going about things the right way and actually understand what I'm doing this time around.

Is it ok to install MediaTomb from Software Centre, if so what's the deal with the icon that is (or isn't installed in the launcher) do I need to run mediatomb from terminal before it will work?

The weird thing is that on the first installation launching MediaTomb using the icon generated the config.xml file that is created on first run. That didn't happen the second time.

So I run mediatomb from terminal using mediatomb, is this the correct and only way needed to start mediatomb and do ignore the fact that running /etc/init.d/mediatomb start gave me a fail?

With default installation settings will MediaTomb start on each boot of the PC? Or do I need to run mediatomb from terminal

I'm little confused about daemon mode, when should I use this?

Big thanks for making it through this wall of text, I'll greatly appreciate any assistance with getting this rectified and returning to sanity.

---

### Post by KC_kid on 2011-11-09
Did you ever get mediatomb to install correctly, make a new config file and run properly??  I am having the exact same situation happening to me and I am at a loss...  Doing google searches for 2 days now, this is the only thread that is the exact same as my problem.
So did you come up with a solution? 
Thanks so much for any help!!

---

### Post by ltworf13 on 2011-12-25
When I type Start Mediatomb in Terminal I get the follow:

 <MSG> start: Rejected send message, 1 matched rules; type="method_call", sender=":1.65" (uid=1000 pid=3340 comm="start mediatomb ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init") <MSG>

---

