---
title: "is Ubuntu One working at all?"
date: 2010-10-10
forum: Ubuntu One (CLOSED)
---

### Post by bro on 2010-10-10
Just upgraded to Maverick, I heard some good stories about updates on Ubuntu One so I clicked it in the memenu and logged in. After that I put several thousands of small files (around 1Gb) into my Ubuntu One folder. 
1) My processor is taken for 100% slowing down my computer
2) None or not much upload activity is happening
3) There is no indicator icon telling me what it is doing
4) The links to one.ubuntu.com/account in the ubuntu one preferences are not working. 

@1) Something start flickering in my window list on the panel saying 'out of space' (not the case). I sync tens of thousands of files (around 25Gb) with Dropbox and Dropbox slows down my computer after startup because it starts syncing/indexing, but not as much as this. It should not happen. 

@2)  To avoid 1) I tried again with less files. Around 1200 files/14Mb, I can use my computer now, but after 20 minutes or so, they have not uploaded yet. One the U1 site the folder structure is visible, though. Is this normal? How long does the indexing and such take before it will upload the files? Has anyone ever got lucky with a few Gb?

@3) Where/how can I get this indicator on my panel? I think I saw it in the past somewhere. Is there not supposed to be an icon giving user feedback on what's happening?

---

### Post by duanedesign on 2010-10-11
There are a couple options for getting more info.

**u1sdtool**
From the command line you can get the number of items in the queue with these commands run in the terminal:

```
u1sdtool --waiting-metadata | wc -l
```

and

```
u1sdtool --waiting-content | wc -l
```

you can track progress as the numbers get smaller. It syncs metadata first (folder structure) then content. You can remove the '| wc -l' from the command to get more details about the items in the queue.

A good wiki page that provides information on using u1sdtool to get more info from Ubuntu One.
[Ubuntu One Client Control]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl")

**magicicada**
There is also a project called [Magicicada]("https://launchpad.net/magicicada") that is a GUI for the Ubuntu One syncdaemon. It allows you to connect/disconnect and see the queue. You can install it with these commands in a terminal:

add the ppa
```
sudo add-apt-repository  ppa:chicharreros/ppa
```
install
```
sudo apt-get update; sudo apt-get install magicicada
```
You can launch the application from Applications > Accessories > Magicicada

**ubuntuone-indicator**
Lastly there is a project that brings back the indicator some may remember from early versions of Ubuntu One. You can install it with these commands run in the terminal:

add the ppa
```
sudo add-apt-repository ppa:rye/ubuntuone-extras
```
install
```
sudo apt-get update; sudo apt-get install ubuntuone-indicator
```
to run the app issue this command
```
ubuntuone-indicator
```

You can add this command to System > Preferences > Startup Applications.

thank you,
duanedesign

---

### Post by bro on 2010-10-11
Thanks, looks like useful info. I might look into it. It seems though I don't have the patience for U1 one yet. It is slowly reducing the number with the waiting-metadata command after I deleted all data from the folder. 

Meanwhile the one small file I put in new, is not uploading yet (the waiting-content still gives '1'). I'm not the kind of guy that gets out of his way to get software working that appears just broken.

Maybe I'll do a fresh install with 11.04, we'll see then.

---

### Post by duanedesign on 2010-10-12
It will not work on the content queue until it has processed all the metadata queue. So the 'one small file' will not be uploaded until --waiting-metadata is 0.

~duanedesign

---

### Post by The Bright Side on 2010-10-12
Yeah I'm really dumbfounded about U1, I have to say. I decided to give it a shot in 10.10 and abandoned it pretty quickly. I'm going back to Dropbox for now. This is what I found:

[LIST=1]
[*]I cannot place the Ubuntu One folder where I want it
[*]That annoying pink "sync folder with Ubuntu One" ribbon shows up in Nautilus even when I select "Hide Ribbon" (check out the bug report about it: [https://bugs.launchpad.net/ubuntuone-client/+bug/657913](https://bugs.launchpad.net/ubuntuone-client/+bug/657913) - the answer pretty much says "yeah it doesn't disappear because it doesn't disappear")
[*]By default, there's no indicator about syncing progress
[*]Overall, it looks and feels like a beta version. There are hardly any config options!
[/LIST]

It's a bit like the overall problem with Ubuntu: they keep adding bells and whistles instead of making their stuff stable and user-friendly.

Same thing with the Software Center: it looks neat, but I have to click on "More Info" to see an application's version number? And then I have to install them one by one? Please. Synaptic has it all in a nice table view, I can just mark the applications I want, click "apply" and get a drink while they're all installed at once. How is the Software Center any better?

Anyway, just rambling.

---

### Post by jimbo99 on 2010-10-13
> **The Bright Side said:**
> Yeah I'm really dumbfounded about U1, I have to say. I decided to give it a shot in 10.10 and abandoned it pretty quickly. I'm going back to Dropbox for now. This is what I found:

[LIST=1]
[*]I cannot place the Ubuntu One folder where I want it
[*]That annoying pink "sync folder with Ubuntu One" ribbon shows up in Nautilus even when I select "Hide Ribbon" (check out the bug report about it: [https://bugs.launchpad.net/ubuntuone-client/+bug/657913](https://bugs.launchpad.net/ubuntuone-client/+bug/657913) - the answer pretty much says "yeah it doesn't disappear because it doesn't disappear")
[*]By default, there's no indicator about syncing progress
[*]Overall, it looks and feels like a beta version. There are hardly any config options!
[/LIST]

It's a bit like the overall problem with Ubuntu: they keep adding bells and whistles instead of making their stuff stable and user-friendly.

Same thing with the Software Center: it looks neat, but I have to click on "More Info" to see an application's version number? And then I have to install them one by one? Please. Synaptic has it all in a nice table view, I can just mark the applications I want, click "apply" and get a drink while they're all installed at once. How is the Software Center any better?

Anyway, just rambling.

I can agree with quite a bit of what you are saying.  That's the nature of Linux.  That would be the common retort.  It is free afterall.  That would be the second retort.  But for the life of me I can't figure out the reasoning behind the color choices.  I would ask myself "who is interfering (at Canonical) with the progress of this?".  Certainly the vast majority of people would not chose these colors.  I thought Mark Shuttleworth was trying to beautify Linux.  He's said as much.  So, why after years is it still as odd as it was back then?

The ribbon thing you mention is annoying.  I'm not sure what it is really intended to do.  You can download a program that will give you information on the progress of your transfers.

I bought a 20gig packages to support Canonical.  I buy music to support them too.  Keep the money coming in and they can afford to do more.  Though I think some personnel changes might be in order, just to get rid of these awful color schemes and to bring some consistency and beauty to Ubuntu.

---

### Post by TheCarl on 2010-10-14
> **bro said:**
> 
1) My processor is taken for 100% slowing down my computer
2) None or not much upload activity is happening
3) There is no indicator icon telling me what it is doing
4) The links to one.ubuntu.com/account in the ubuntu one preferences are not working. 


My experience was the same, it seems U1 is still in beta.
Dropbox is alot smoother, but I guess I'll upgrade my U1 account
and use dropbox mainly for sharing with friends and such

---

