---
title: "strange apache question -can it be done?"
date: 2007-11-14
forum: Server Platforms
---

### Post by prezbedard on 2007-11-14
ok I'm not sure this can be done but...

This is for testing. Is it possible to host website(s) using apache but have the actual dir/files on a different computer?

I'd like to setup a testing server for our development team but don't want to interupt the work by moving all the data off the current server.

So one lower end machine will be running an apache webserver for testing the sites before going live and another will hold the data for each website.

Thanks.

---

### Post by Bliepo32 on 2007-11-14
I am quite sure that this is possible, although I do not know how. My bet would be make a network, use a network harddrive, and mount it as /apache or something.

---

### Post by prezbedard on 2007-11-14
I have everything in place. I just am not sure how do this since I have only played with apache very little i.e. I can install and get it running then stops there. So all I need is steps to make it happen. :)

---

### Post by prezbedard on 2007-11-15
ok so I've read through the apache read me and config files and numerous posts I do have a better idea how it works.

Would I need samba installed on the web server to mount the dir if the sites  folders and files were being stored on a windows server?

Thanks,

---

### Post by jflaker on 2007-11-15
> **prezbedard said:**
> ok I'm not sure this can be done but...

This is for testing. Is it possible to host website(s) using apache but have the actual dir/files on a different computer?

I'd like to setup a testing server for our development team but don't want to interupt the work by moving all the data off the current server.

So one lower end machine will be running an apache webserver for testing the sites before going live and another will hold the data for each website.

Thanks.

I believe that this is not allowed.  Even if it were, I would advise you to  use local directories as your Apache directories as relying on another network resource is, for reliability reasons, not recommended.

Your best bet is to test, then move your files to production servers when they are ready for prime-time.

---

### Post by fry15 on 2007-11-15
you would need samba client installed on the server to access the windows file share that you would have set up on the windows server.

you can then mount the fileshare automatically by editing the /etc/fstab file. more info about how to do that can be found here:
[http://web.archive.org/web/20051231035314/http://www.ubuntuguide.org/#automountnetworkfolders](http://web.archive.org/web/20051231035314/http://www.ubuntuguide.org/#automountnetworkfolders)


hope this helps!

---

### Post by prezbedard on 2007-11-15
This is all for testing anyway live stuff either goes to our website or the clients host.

thanks for the tip I was thinking I had to install the complete samba package.

I'll post back with feedback

---

### Post by idiotsruleintheshowerjane on 2007-11-16
nfs with nfsmount 'might' be able to accomplish your  goal.  yes,  agreed, nfs ain't  'secure'.

j_k

---

