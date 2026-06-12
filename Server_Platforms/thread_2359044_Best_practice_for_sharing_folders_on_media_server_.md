---
title: "Best practice for sharing folders on media server (mix of Linux and Windows clients)"
date: 2017-04-20
forum: Server Platforms
---

### Post by elsmandino2 on 2017-04-20
Hello,

I have finally got ubuntu server fully up and running, mounted a hard drive with fstab and created a directory on the hard drive called "Videos".

I want "Videos" to be available to a Raspberry Pi, a laptop running Linux and a Windows-based desktop.

Am I correct in thinking that it makes sense to share the folder via both Samba and NFS?  I.e. access the folder via NFS with the RPi and laptop and Samba for the desktop machine?

---

### Post by slickymaster on 2017-04-20
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2017-04-20
yes. NFS is faster than samba and provides native permissions.

However, you could run a media server to get more flexible access for different clients over other protocols. DLNA via Plex Server, for example.  Or run all 3 of those things.  Plex can transcode videos on-the-fly to codecs required by the different types of clients.  For example, a r-pi can't handle hidef h.265 content - no hardware decoding for that v-codec.  OTOH, h.264 is well supported by the r-pi hardware, so transcoding anything that isn't h.264 into that specific v-codec is helpful for r-pis.  It is also what 2nd-generation Roku and other streaming devices prefer - so mpeg2, xvid, divx, flv, mov, and h.265 content can be transcoded for those other, highly-limited, devices.

---

### Post by elsmandino2 on 2017-04-20
Thank you - I have done a bit more research and see, now, that SAMBA and NFS are only two of a number of protocols that I could use.

I think I will do some testing with NFS, just to see if I can get it up and running and then start experimenting with some of the others.

I have done a bit of research on NFS and came across this guide:

[http://forum.kodi.tv/showthread.php?tid=175097](http://forum.kodi.tv/showthread.php?tid=175097)

Just to be absolutely clear before I do anything (I am still so worried about hosing my newly set up server), am I correct that I need to do the following:

```
[COLOR=#000000][FONT=monospace]sudo apt-get install nfs-kernel-server[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]sudo nano /etc/exports[/FONT][/COLOR]
```[COLOR=#000000][FONT=monospace]

As my folder to be shared is /media/video and my RPi IP address is 192.168.1.11, type

/media/video 192.168.1.11 [/FONT][/COLOR][COLOR=#000000][FONT=monospace](rw,no_subtree_check,async,insecure)[/FONT][/COLOR][COLOR=#000000][FONT=monospace]

[/FONT][/COLOR][COLOR=#000000][FONT=monospace]Save and exit and then 

[/FONT][/COLOR][COLOR=#000000][FONT=monospace]```
sudo service nfs-kernel-server restart
```

Is that all I need to do?

If so, how would I add an additional Rpi with IP address 192.168.1.12?

Do you have to add a separate line for each IP address or can you an additional one to the same line?[/FONT][/COLOR]

---

### Post by TheFu on 2017-04-20
In the Unix world, protocols tend to work cross-platform, since the code base is the same (or nearly the same).  

That kodi.xxx link seams reasonable for a non-secure setup.  Letting media center NFS clients have read-write access probably isn't smart, at least initially. Lots of other details they left out.  'sudo nano' ... really should be **sudoedit**, though that doesn't matter much, provided the editor is NOT a GUI editor.

To setup an NFS server on ubuntu, I'd google "*nfs server ubuntu*", find the help.ubuntu.com link and follow those instruction. Depending on the version and options you decide, it may be more involved.  v3 of NFS doesn't have much security, really just the IP. With NFSv4, kerberos and encryption were added.  With kerberos, you can do server-to-server authentication.

If I needed to do something a little more than that page shows, I'd delve into the manpage for every part of the subsystem involved.  For example, almost every config file has a manpage with fantastic information. **man exports** for example. This is always better than trusting what someone like me says in a forum.  The manpages are better than any other document if there are any questions.

On the client-side, for kodi specifically, just use the GUI to make the NFS connection(s).  But beware that UID/GUI numbers from the different systems need to match for the users accessing the data over NFS.  The 'id' command will show those.  Root doesn't get any special access - so using sudo on NFS storage doesn't work (well, that isn't entirely true, but ... ).

In the amount of time you've waited for a response, you could have tried it.  It does work, but you don't need different lines. Or you can use a netmask to cover lots of clients if you don't bother with kerberos, but from a security standpoint, it is probably best to specifically limit by IP/hostname and setup kerberos.

With most things Unixy, there is what you *CAN* do and what you *SHOULD* do.  Only you can decide which is best for your needs.  You CAN use NFSv3, but you SHOULD use NFSv4 w/ Kerberos.

---

### Post by SeijiSensei on 2017-04-20
You'll also need to install the **nfs-common** package on the Linux clients.

My home server uses NFSv3 without Kerberos because the server is not exposed to outside users in any way.

You can support an entire IP subnet in /etc/exports like this:

```
/media/video 192.168.1.0/24(rw,no_subtree_check,async,insecure)
```

Now any address starting with 192.168.1 will be permitted.

---

### Post by elsmandino2 on 2017-04-21
> **SeijiSensei said:**
> 
My home server uses NFSv3 without Kerberos because the server is not exposed to outside users in any way.


I see - so NFSv3 is fine, as long as you don't try and set up your server for accessing from outside your local network?

Is the bit in brackets above - i.e. (rw,no_subtree_check,async,insecure), the suggested setting that I should be using or was this just an example?

---

### Post by TheFu on 2017-04-21
> **elsmandino2 said:**
> I see - so NFSv3 is fine, as long as you don't try and set up your server for accessing from outside your local network?
Whether is it fine or not, only you can say. You know the risk factors on your network and other systems.  Many people in home environments do only use NFSv3.  Do they all know how little security that provides?  Probably not, because they found some guide somewhere that didn't care about security at all.

> **elsmandino2 said:**
> Is the bit in brackets above - i.e. (rw,no_subtree_check,async,insecure), the suggested setting that I should be using or was this just an example?

There are different reasons to pick each option of the available options.  For example, I would never use NFS over wifi with a read-write mount, but lots of people here do all the time.  I've seen corrupted files doing that. There are lots of choices and the 5 minutes of reading the manpage is well worth your time, IMHO.
I use: (rw,root_squash,async) for my wired systems.  If I were running a DB on NFS storage, I'd use sync, not async.  It just depends.  The root_squash is a reminder for me.  **man exports** will show the available options. There is an example section there.

The closest that I know for "recommended" is in the ubuntu help pages.  Redhat might recommend other options, for different reasons.  Just remember - working does not necessary mean *secure*.

---

### Post by SeijiSensei on 2017-04-21
> **elsmandino2 said:**
> Is the bit in brackets above - i.e. (rw,no_subtree_check,async,insecure), the suggested setting that I should be using or was this just an example?
Those were the options you gave in your post #4 above.  

I use "(rw,no_root_squash,async,insecure)."  I export /home off the server but mount it as root in a directory under /media.  I can't do that without no_root_squash.  I've used async over wifi for years now without incident, though my server is connected to an uninterruptible power supply so a loss of power won't result in a corrupted file.  Using "sync" over wifi will cause lengthy delays when copying files to the server. (Wifi is a "half-duplex" connection, so data can flow in only one direction at a time unlike full-duplex Ethernet with separate transmit and receive pairs.)

As for security, my wifi router uses an extremely long passphrase so I'm not worried about neighbors gaining access to my network.  The only clients that can see my NFS server are all inside my home.  I could lock it down further by specifying a list of MAC addresses allowed to connect to my router, but I've had no reason to do so.

---

