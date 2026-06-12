---
title: "iTunes library residing on Ubuntu"
date: 2007-02-27
forum: Server Platforms
---

### Post by jeb00d on 2007-02-27
It's been a long road to this point so ill do my best to give everyone the required detail.

My goal is to have my iTunes library reside on a network share.  I want to use OS X to manage the library.  I'm running Edgy and the most recent version of OS X Tiger and iTunes.

Here's what has hapened to this point.  I set up a samba share on a folder called Media on the Edgy box which I can access just fine.  I copied all my music to that folder.  Here's where the fun starts.

I sucessfully exported my itunes.xml file to the networked folder and edited it to reflect the network share address.  At this point I imported the library and waited the painful couple of hours it took to import and 'determine gapless information'  after that was done, everything worked....until the next day when I got an error that iTunes couldn't find the library on the network share.

After some inspection I discovered that the file permissions had all the subdirectories locked down and their ownership was 'nobody'.  

I entered nautilus as root and edited the permissions to the greatest allowable access recursively.  

At this point (on the edgy box...not using the mac) I created a sub folder called itunes_music and put all media folders in there.  I re-edited the itunes xml file to reflect this and reimported the library again.

Now comes the wonky part.  This morning, I mounted the Media folder and fired up iTunes which gave me the terrifying error of 'cannot find itunes library in specified folder'.  I sat down at the edgy box and I was shocked to see that not only was there no iTunes library there....the files which had been placed in /media/itunes_music/ weren't there anymore.  They had moved back to the /media/ folder.

How in the world did this happen?  Is there a problem with ownership?  Do I need to somehow set up a separate user for my macbok pro to access the folder (never had to do that with my LAMP server)?

I'm utterly confounded at how ubuntu could act on its own to undo the changes I made last night.

Thanks,

---

### Post by WelterPelter on 2007-03-02
I have successfully done exactly what you are trying to do. 
MacBook Pro, Ubuntu, Samba. It works.
I don't have time right now to help you debug your setup.
But my hunch is that you just have to get samba working properly (permissions, etc.) for normal file transfer, and then everything will be OK with iTunes.
In other words, fully debug your Samba setup first. Then it will work.
Best,
M.

---

