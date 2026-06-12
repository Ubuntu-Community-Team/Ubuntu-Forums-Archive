---
title: "Adding NIC to Server"
date: 2010-01-15
forum: Server Platforms
---

### Post by spynappels on 2010-01-15
Hi Guys,

This probably sounds like a stupid question, but I need to add a NIC to an existing server running Ubuntu Server edition 8.10. My question is what changes I need to make once the NIC is physically installed? I guess it will not be autoconfigured, so I will have to add it to the /etc/network/interfaces manually, which is ok as I need to set it up with a static interface anyway.

Is there a good How-to or set of instructions on how to do this?

I can explain the scenario further if required....

Thanks

---

### Post by gobbledigook on 2010-01-15
hi! 

Adding a new nic is quite easy! just plug it in and when you boot it 'should' be automagically picked up :) As you suggest you just amend your interfaces file with the new details... I did this a while back and had issues with configuring half/full duplexing, check [**_this _**]("http://ubuntuforums.org/showthread.php?t=1161465")thread and you can see how i got it working :)

---

