---
title: "Protected files on a hard drive"
date: 2011-11-02
forum: Security
---

### Post by quantumelody on 2011-11-02
I think this is security-related, but I'm sure it will be moved if it's in the wrong place. :) 

My computer's motherboard died, and there are some files that I really need to get off of the hard drive so I can work. The files are in a .something directory, which I need to copy to the directory I am currently working under on a different computer. However, because one of the files is protected, I can't actually transfer that one to the new .something directory. I tried to boot the OS using a usb-connected case to change the permissions &c, but the boot failed both times I tried. Is there another way to grab the file?

I'm also not really sure what kind of terminology I should be using for this, as all of my searches on the forums came up with nothing.

Thanks in advance for the help.

---

### Post by HermanAB on 2011-11-03
Howdy,

Try booting a LiveCD (Ubuntu or Knoppix install CD).

Something like this:
$ sudo cp -a /whereitis/.something /whereyouwant/.

Read the cp man page for details.

When all else fails, put the disk in a working machine.

---

