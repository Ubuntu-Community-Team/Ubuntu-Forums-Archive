---
title: "&quot;What&quot; and &quot;When&quot; to virtualize"
date: 2008-06-06
forum: Server Platforms
---

### Post by TheGameAh on 2008-06-06
Hey guys.  Just looking for opinions/best practices.

Recently built a 500 G RAID 10 server that I will use a auxiliary storage.  Just installed Samba, put a few shares on it, let it fly.

Then I said, well, I have the extra space, let me move a few VMs to it.  

So now I have a Blackberry server, a Windows XP client, and a Samba server, all running on the same box.

Now, I didn't virtualize the Samba server.  It's just running, happy as can be.  "Should" I have created a VM for this samba box?  "Why" would I want to?  Just curious as to what others might have done.  From what I've always done, I've only virtualized relatively static machines.  Such as a blackberry server for example.  It just sits there and pushes emails. Occasionally add or delete a user.

Now this samba file share will hold close to 200 gigs.  That's a very big virtual disk to create.  Is it worth it?  

So I was wondering what you guys put in your VMs, and what you didn't.

---

### Post by gtdaqua on 2008-06-06
You are right. It should be ok to have a Samba server on the Host. The only concern is the host has to be really light-weight so it will simply 'stand' the test of time! 

You could create a separate VM with Openfiler 64 bit on it and use iSCSI to configure a samba storage. I was on Openfiler for sometime and its pretty good and stable. 

No prob with creating a single 200GB virtual disk file. It should be ok. I am using two sets of 250GB virtual disks and have had no problems.

---

