---
title: "What do you think about Ubuntu's Networking readiness?"
date: 2012-07-07
forum: The Cafe
---

### Post by 0c-bill on 2012-07-07
I have to declare that I have wasted so many hours troubleshooting issues with basic networking features of Ubuntu, that I must question the maturity and readiness of the distribution.

Just to start the thread two cases:

1) A small change of the default samba.conf file from the 11.04 repository where the order of the host resolution caused any lan with two or more samba machines on it to not be able to connect with any samba share....

2) A problem with both 11.04 and 12.04 where libavahi-compat-libdnssd1 is absolutely necessary for mdns to function correctly on a stock installation.

And sooo little in the way of clear or readily available documetation of how each distribution's basic packages deviate from their stock sources (which would have saved me HOURS of frustration).

So.. what do you think?  What issues have you encountered?  And, more importantly, do you have any ideas of how to fix this ongoing problem with Ubuntu's networking for the little guy?

---

### Post by HermanAB on 2012-07-07
Well, I spot two big mistakes on your part right there:
1. Samba and
2. Avahi

Other than those two mostly useless programs, Linux networking works perfectly thank you.

---

### Post by CharlesA on 2012-07-07
> **HermanAB said:**
> 
2. Avahi

I dislike Avahi with a passion. I can understand using it for zero config, but it causes more issues than it solves. At least from my experience.

I haven't had any issues with Samba, but I know there are a ton of threads about it, ranging from permissions, to incorrect smb.conf files to problems with name resolution.

Yuck!

---

### Post by critin on 2012-07-07
> **HermanAB said:**
> Well, I spot two big mistakes on your part right there:
1. Samba and
2. Avahi

Other than those two mostly useless programs, Linux networking works perfectly thank you.

So how do you do it?  Please...
I use Samba, but the network is unreliable from day to day.

---

### Post by CharlesA on 2012-07-07
> **critin said:**
> So how do you do it?  Please...
I use Samba, but the network is unreliable from day to day.
I believe Herman uses NFS.

How do you mean the network in unreliable? Is it slow, or do you have problems pinging/connecting/whatever?

---

### Post by toupeiro on 2012-07-08
I've seen/supported ubuntu servers pushing 10Gbit/sec.  I think a better question is, is *your* network ready for Ubuntu? :popcorn:

Have you researched CIFS rather than smbfs?

---

### Post by HermanAB on 2012-07-08
Windows supports NFS.  

Rather than kerfuffling with Samba to make Linux work with Windows, I find it less of a head-ache to kerfuffle with NFS to make Windows work with Linux.

[http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_programs/nfs-client-for-windows-7/42aae25d-d077-4ff9-abdf-7314a589c46d](http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_programs/nfs-client-for-windows-7/42aae25d-d077-4ff9-abdf-7314a589c46d)

---

### Post by CharlesA on 2012-07-08
> **HermanAB said:**
> Windows supports NFS.  

Rather than kerfuffling with Samba to make Linux work with Windows, I find it less of a head-ache to kerfuffle with NFS to make Windows work with Linux.

[http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_programs/nfs-client-for-windows-7/42aae25d-d077-4ff9-abdf-7314a589c46d](http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_programs/nfs-client-for-windows-7/42aae25d-d077-4ff9-abdf-7314a589c46d)
Thought so. Nice link.

I just use Samba on my box cuz I already have it set up. :p

---

### Post by Gone fishing on 2012-07-08
I've used Samba as a Windows domain server and it was great the only problem was MS changing authentication between Windows releases, however, this was on a sever and not casual sharing. For Linux authentication and sharing I used LDAP and NFS which worked perfectly. /Home on the clients was all server mounted it worked very well.

---

### Post by cariboo on 2012-07-08
0c-bill, I'd suggest you look elsewhere if you are having internal network problems. I run NFS, Samba and most recently minidlna on my server with zero network problems. Over the years when I've had networking problems, it has usually been hardware rather than software that causes problems.

A nic is easy and cheap enough to replace, that it should be one of the first things you check, also check your cabling, especially if you have pets, or the cables are in high traffic areas.

---

### Post by thatguruguy on 2012-07-08
> **cariboo907 said:**
> 0c-bill, I'd suggest you look elsewhere if you are having internal network problems. I run NFS, Samba and most recently minidlna on my server with zero network problems. Over the years when I've had networking problems, it has usually been hardware rather than software that causes problems.

A nic is easy and cheap enough to replace, that it should be one of the first things you check, also check your cabling, especially if you have pets, or the cables are in high traffic areas.

I just recently dumped coherence (which was a resource hog) and started using minidlna. Ridiculously easy to set up, and works great for streaming media to the Android tablets the kids and I use.

I've had zero problems with networking in my house, or using my MythTV setup over http when I'm away from home and feel like streaming my media.

---

### Post by Gone fishing on 2012-07-09
> A nic is easy and cheap enough to replace, that it should be one of the first things you check

I've had problems once with cheap nic cards, however, I always found dlink stuff to work well and is quite cheap.

---

### Post by spynappels on 2012-07-09
I've never had any issues with networking in any of my 200+ production servers running Ubuntu. That includes LACP Bonded interfaces of 4x1GbE on about 50 of these, so networking is fine as far as I can tell.

---

### Post by snip3r8 on 2012-07-09
Saying Ubuntu sucks at networking is like saying the sun is too cold...

---

### Post by critin on 2012-07-10
> **CharlesA said:**
> I believe Herman uses NFS.

How do you mean the network in unreliable? Is it slow, or do you have problems pinging/connecting/whatever?

All of the above except for 'slow' lol   My trouble is all my doing.  When they all work I do something to break one and off we go again.  Ubuntu is stable though, it's the windows that keep taking access permissions away.  I'm learning...

I've been studying these alternate network programs listed here, **I had no idea there was anything other than windows network and Samba. ** I need to find good instructions and see what I can do--I'm reading up on NFS right now and I see there's something in Synaptic--I'm just not sure if it's the entire app.

Samba works well with linux, and I can add windows, I just can't keep from messing with it.  lol

Thanks for all the info.

---

### Post by screaminj3sus on 2012-07-10
I have 0 networking issues in 12.04. I've NEVER had issues with networkmanager, but in past ubuntu releases I have had issues where samba gave me "failed to retrieve share list from server" (works fine in 12.04 though).

---

### Post by cariboo on 2012-07-10
> **critin said:**
> All of the above except for 'slow' lol   My trouble is all my doing.  When they all work I do something to break one and off we go again.  Ubuntu is stable though, it's the windows that keep taking access permissions away.  I'm learning...

I've been studying these alternate network programs listed here, **I had no idea there was anything other than windows network and Samba. ** I need to find good instructions and see what I can do--I'm reading up on NFS right now and I see there's something in Synaptic--I'm just not sure if it's the entire app.

Samba works well with linux, and I can add windows, I just can't keep from messing with it.  lol

Thanks for all the info.

The NFS client is installed by default, so all you need to install is the nfs-kernel-server. When you install it via your favourite method, the dependencies are installed automagically.

---

### Post by critin on 2012-07-11
> **cariboo907 said:**
> The NFS client is installed by default, so all you need to install is the nfs-kernel-server. When you install it via your favourite method, the dependencies are installed automagically.

I wonder why it isn't suggested more often?  Samba is the only thing I've seen mentioned, and it's the program auto added when adding file sharing.   Maybe because it's easier to set up/understand?  Glad to know it's already installed, thanks!

Oh, will Samba interfere with NFS?  Should Samba be uninstalled first?

---

### Post by CharlesA on 2012-07-11
You can use both NFS and Samba on the same box with no problems.

---

### Post by HermanAB on 2012-07-11
NFS is never mentioned because it is so simple - a one liner.

On the server in file /etc/exports add:
/home/whatever 192.168.1.0/24(root_squash,async,rw)
then restart the server.

On the client:
# mount -t nfs 192.168.1.1/home/whatever /mnt/whatever

Note that you should have the same UID and GID on the client and server, unless you use all-squash.

So that is why no-one ever talk about NFS. There is nothing to say!

---

### Post by Morbius1 on 2012-07-11
> **0c-bill said:**
> 1) A small change of the default samba.conf file from the 11.04 repository where the order of the host resolution caused any lan with two or more samba machines on it to not be able to connect with any samba share....
The name resolve order in 11.04 and 12.04 are identical. In fact it's been that way for years so I know of no change.
> 2) A problem with both 11.04 and 12.04 where libavahi-compat-libdnssd1  is absolutely necessary for mdns to function correctly on a stock  installation.
I don't have that package installed and yet mdns works just fine. All the Macs in this menagerie use it to connect to the printer attached to this machine.
> And, more importantly, do you have any ideas of how to fix this ongoing problem with Ubuntu's networking for the little guy?     I have 2:
(1) For the home user smb.conf should be altered to add the following parameter to override the defaults:
```
name resolve order = bcast host lmhosts wins
```(2) The installer should prevent users from creating host names in excess of 15 characters in length. If it cannot prevent them from doing so then it should warn them about doing so. There's actually a bug report that states they'll get around to it someday: [https://bugs.launchpad.net/ubuntu/precise/+source/samba/+bug/735072](https://bugs.launchpad.net/ubuntu/precise/+source/samba/+bug/735072)

I'd bet that the vast majority of samba "browsing" issues would be eliminated with these 2 changes. 

Of course you are always free to connect to a samba server by ip address or using mdns ( i.e., host.local ) and not browse to one at all.

---

### Post by Morbius1 on 2012-07-11
> **HermanAB said:**
> NFS is never mentioned because it is so simple - a one liner.

On the server in file /etc/exports add:
/home/whatever 192.168.1.0/24(root_squash,async,rw)
then restart the server.

On the client:
# mount -t nfs 192.168.1.1/home/whatever /mnt/whatever

Note that you should have the same UID and GID on the client and server, unless you use all-squash.

So that is why no-one ever talk about NFS. There is nothing to say!
Oh, so it's like when you do samba this way:

On the server:
net usershare add documents /home/morbius/Documents "documents" username:F guest_ok=y

On the client:
gvfs-mount smb://192.168.0.100/documents

---

### Post by SeijiSensei on 2012-07-11
> **HermanAB said:**
> NFS is never mentioned because it is so simple - a one liner.

I think it has more to do with expectation that the client machines will likely be running Windows.  While it's possible to install the [Windows NFS client]("http://www.microsoft.com/en-us/download/details.aspx?id=2391"), that's not as easy as using Samba to serve files with CIFS.  Windows users can then employ standard techniques like mapping a network drive or using UNC share paths like \\server\share.

---

### Post by CharlesA on 2012-07-11
> **SeijiSensei said:**
> I think it has more to do with expectation that the client machines will likely be running Windows.  While it's possible to install the [Windows NFS client]("http://www.microsoft.com/en-us/download/details.aspx?id=2391"), that's not as easy as using Samba to serve files with CIFS.  Windows users can then employ standard techniques like mapping a network drive or using UNC share paths like \\server\share.
That's why I use Samba vs NFS at home - the less client configuration I have to do the better.

---

### Post by critin on 2012-07-11
>  Herman:  So that is why no-one ever talk about NFS. There is nothing to say!

lol-- nothing for those who already know maybe.  As a beginner, I've never heard of the alternative, at least not in words that I could understand.  You know--layman's terms?    I'm still reading and studying.  

Your post helps--thanks.

---

### Post by 0c-bill on 2012-08-01
As I haven't learned how to edit my posts yet (could be a feature unavailable to newbies...). I'll post here.

This discussion is very informative so far!

I'd like to retract the point about needing the compat library for mdns.  Turns out that my new D-Link router may be the issue.  Having done alot of googling; found out that D-Link routers have a historical problem with making messages involving .local domain.

There is, apparently,  a feature built into standard mdns that has the server kill itself if it thinks it might be interfering with another, non-mdns, domain server.  This apparently is a default feature that doesn't bother to check what name is actually being used.  

Sorry for the confusion on my part.  

I noticed a post by MORBIUS 1 concerning a change to the domain name resolution line of a samba config file.  Morbius definitely knows his tcp/ip!

That file was not configured properly in the initial install from the UBUNTU reps. on my pc. Too bad I didn't know it at the time.

 I finally gave up on the problem.  BUT it caused me to actually learn about tcp/ip.  80 pages into TCP/IP for Dummies and the reason for my samba problem hit me...   As far as I can make out, that config file was edited by the Ubuntu maintaner.  I say this because the samba site shows the default for it being similar to Morbius post above.  Whereas the file installed on my machine from the repositories had a tag in it that essentially caused the second half of the line to be ignored during the resolution process.  That meant "bcast" would often get skipped over. And "bcast" is what makes smb so useful in a small network.


Thank you for all the chat so far!

---

