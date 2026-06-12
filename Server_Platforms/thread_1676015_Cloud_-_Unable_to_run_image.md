---
title: "Cloud - Unable to run image"
date: 2011-01-26
forum: Server Platforms
---

### Post by Mando_be on 2011-01-26
I've been experimenting with setting up a private cloud using Ubuntu Cloud. However I'm having some trouble running an image.

So I've downloaded an image using the store and set up all the necessary keys of the server and the node but when I try to run the image using (executed on the node):
```
euca-run-instances -k mykey emi-E00A1081
```
And then view the instances on the server using
```
watch -n5 euca-describe-instances
```
The instance I wanted to run just stays on pending for a couple of minutes and afterwards it just says 'terminated'.

I was hoping if someone could perhaps explain what could have gone wrong or how I could see the log files on the server for example.

Here's my current setup:
[INDENT]1 Virtual Cloud Controller Server (VMWARE Player)
1 Virtual Cloud Node (VMWare Player)[/INDENT]

---

