---
title: "Confusing apache thing(atleast for me)"
date: 2009-04-02
forum: Server Platforms
---

### Post by jigglywiggly on 2009-04-02
So here is what is happening, I run 2 VMs on a server 2003 enterprise computer. One of them is an apache server that hosts my main website, and I also use webmin to manage it. Then I run another server 2003 enterprise virtual machine which hosts my https file transfer server. So basically here is my goal, I want to host a second site(another index.html if you will) EG I want it to do this mywebsite.com/rawr/index.html or something similar. So I have 2 options to try and do this, because I need the https file server to be able to access these directories as well as linux. But I can't figure out webmin how to handle a smb directory correctly? So then I thought about just putting the website stuff on the linux machine, however the windows computers can't see the linux machine. So how would I be able to map network a linux drive from within windows? I can't see the linux pc in the network, but the linux pc can see them. 

So basically

1. Figure out how to use webmin to handle a smb directory.
2. OR figure out how the linux pc to be accesible by windows computers.

Thanks a bunch.

---

### Post by jigglywiggly on 2009-04-02
Oh and I'm also confused how I would get it to access the files from smb://wndowscomputer/directory how would it know how to acess that? Like How would I make [www.whatever.com/directory/index.html](www.whatever.com/directory/index.html) point to smb://wndowscomputer/directory/index.html
Because I am already hosting my default site on my local C drive and that is [www.whatever.com](www.whatever.com) 
Does this sort of make sense? IIS 6.0 is a lot easier to use D:

---

