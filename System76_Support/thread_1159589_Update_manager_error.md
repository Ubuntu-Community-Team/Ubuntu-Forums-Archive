---
title: "Update manager error"
date: 2009-05-14
forum: System76 Support
---

### Post by ewg on 2009-05-14
SYSTEM 76 Sable, Ubuntu 9.04

I keep getting the triangle icon for update notification. When I run it nothing happens and the message box with the icon suggests running check for updates. When I do I get this:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages)  404 Not Found [IP: 91.189.88.46 80] 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.88.46 80] 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.46 80] 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.88.46 80] 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources)  404 Not Found [IP: 91.189.88.46 80] 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources)  404 Not Found [IP: 91.189.88.46 80] 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources)  404 Not Found [IP: 91.189.88.46 80] 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.46 80] 
Some index files failed to download, they have been ignored, or old ones used instead.

What's up?
Thanks,

---

### Post by jml on 2009-05-14
Have you confirmed that you are actually on a live network?  The last time I got a message like that one occurred when my cable modem hung and needed to be reset. Since my wireless access point was working correctly,I did not see any warning from NetworkManager.  It was only when I realized that I could not connect to anything, that I realized what the problem was.

If your internet access is working well, another possibility is that the update servers may be down for some reason.

Joe

---

### Post by Spinitch on 2009-05-14
ive been getting the same error canonical and security they all fail for update but i will try to reboot my router see if that works if not i haveno idea as ive not been able to run my pc after rebooting from a jaunty update after installing and rebooting

---

### Post by ewg on 2009-05-15
Thanks for the replies. My internet connection is good.

I should point out that the truncated version of the error message I posted left out (this is each line of the message.)
us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe



Don't understand why it's still trying to get gutsy when I'm up to Jaunty.

Thanks,

---

### Post by Lee_Machine on 2009-05-15
Go to System >> Admin >> Software Sources

Under the Updates tab is Unsupported Updates (Jaunty Backports) checked off?

Have you been updating since Gutsy? 

Also under the Third Party Software tab is [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) checked? 

Support for Gutsy ended April 18, 2009...so that would explain why the servers don't exist. After a few weeks they are taken down completely.

---

### Post by ewg on 2009-05-15
Lee, thanks for the reply.

Yes to all of your questions.

I have all updates since gusty and those boxes are checked.

---

### Post by Lee_Machine on 2009-05-15
k, well go ahead and uncheck the archive one

Also to clarify, have you been doing the 6 month cycle of Upgrading the OS? Gutsy >> Hardy >> Intrepid >> Jaunty 


Lastly in terminal do this: sudo gedit etc/apt/sources.list

Do you have anything is there pointing to Gutsy repos?

It will look like this:

deb [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages:/ gutsy](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages:/ gutsy)

It will not be in a comment as designated with ##

if so delete it and click save

this goes for any other version you may have that is not Jaunty.

If you made any changes do a 

sudo apt-get update

---

### Post by ewg on 2009-05-16
Thanks Lee,
Yes,I have always done the 6 month upgrade.
I unchecked the gutsy archived.
The source list actually showed nothing (was blank).

I'll let you know if it keeps popping up.

---

### Post by Lee_Machine on 2009-05-16
oh i left out a forward slash

sudo gedit /etc/apt/sources.list

that will work

WOW that has the be the longest upgrade cycle I have heard of. I'm quite surprised this is your only issue. :p

---

### Post by ewg on 2009-05-16
Yeah, I always wait 2 weeks post release before I upgrade and really have had only minor issues.

Thanks again,

---

