---
title: "School network, net logon help?"
date: 2007-02-11
forum: Server Platforms
---

### Post by iamacarpetlicker on 2007-02-11
Hey,
Okay, me and a few friends at the local LUG are trying to convert our school to Linux or at least switch to Linux servers.
But first we are going to convert a primary school for some experience, and I need some help planning as I dont have experience with network login on Linux networks.
I cant find anything on Google, but what is the best way to network around 100 computers with networked logon and files stored at a central location?
I have heard LDAP is good for auth, and I was also thinking maybe if I mounted "/home" over NFS that would work. But I'm not to sure, could anyone give me any pointers please?

We are going to be using Ubuntu Server edition for the server, Edubuntu for the kids machines, and Ubuntu for the staff. Also we might need to have windows compatibility, but I understand that windows has an NFS client so that shouldn't be a problem.

Hope that made sense, and any help would be highly appreciated!
Thanks,
Sam.

---

### Post by caveman56 on 2007-02-12
Hey there, I'm working on much the same thing at the school I teach at.  I've decided, with the input of others here on the forum to adopt the NFS method.  Seems to work pretty well mounting /home across nfs.  Gives the students all their files and desktop on any computer they log into.  Just starting to play with it myself in preperation for the next school year.  Would love to know what you decide to use, maybe compare notes.

later,

Dave

---

### Post by iamacarpetlicker on 2007-02-12
Thanks for the reply Dave =].
I think the NFS method does sound good, and I guess the permissions will be very tight that way? Which especially for a primary school should be very good.
Can I just ask how and if your doing network logon? Because I'm really not sure on how to do it, that's the hard part for me. I know of LDAP and Kerberos but I don't know how-to go about using then and if they are any good. I know the macs at my school use LDAP so I'm thinking that's a good method?

Good luck implementing it all at your school, and yes it would be good to compare notes. Just got to get the rest of the LUG joining in a bit more, and convince a primary school that Ubuntu is better than windows =\.

Oh and also, I know schools have to use certain programs as part of the curriculum...I haven't booted edubuntu yet, but being a teacher, could you tell me if all the programs needed are there? Sorry, just don't want to look like a fool when doing the presentation to the school =/.

Thanks lots,
Sam.

---

### Post by jtc on 2007-02-12
> **iamacarpetlicker said:**
> I think the NFS method does sound good, and I guess the permissions will be very tight that way?
Yes and no. You do have the full set of permissions-settings to use, but on the hand hand, when it comes to security then plain NFS is far from bulletproof. Basically it comes down to your more or less having to trust the clients fully.

Of course, you can always integrate NFS into Kerberos.

That is something I plan to do anytime soon now :roll:

---

