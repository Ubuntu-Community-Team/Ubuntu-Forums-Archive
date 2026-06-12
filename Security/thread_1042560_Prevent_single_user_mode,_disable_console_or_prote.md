---
title: "Prevent single user mode, disable console or protect grub?"
date: 2009-01-17
forum: Security
---

### Post by IMNOboist on 2009-01-17
I'm working on a business concept and there's one big problem staring me in the face that I need to get figured out.

Basically, I'm going to be sending mini-ITX computers to customers to do whatever they need them to. However, I don't want them to be able to touch anything. I understand that they can pull the HDD, but I have that much figured out. But I can't think of any way to prevent them from plugging a monitor and keyboard in and booting into single user mode and going to town. 

Here's the only ways I can think of to prevent this:
1. Make it so the computer can't be booted into single user mode.
2. Completely disabling the console (leaving SSH available).
3. Somehow prevent changes to the grub configuration so they can't get into single user mode.

I'm sure those aren't the only solutions, so I'd be willing to try others, but I don't know if any that I've listed are even possible or effective.

The data on the HDD isn't that important, I just don't want some Linux-know-it-all employee of one of my customers to get into the box and screw it up or even worse, turn it into some zombie box.

Thanks for all of your help!

---

### Post by Achetar on 2009-01-17
It is possible to write a program that gets launched on boot instead of login. A dummy app is not hard. Sample C code:

```

int main(int * argc, char * argv)
{
        //Do nothing
        return 0;
}

```

Not guaranteed to work, I wrote it on the fly. It should do nothing then exit.

---

### Post by IMNOboist on 2009-01-17
That's an interesting approach, but I would need SSH access and I think that would prevent that as well.

---

### Post by lswb on 2009-01-17
> **IMNOboist said:**
> I'm working on a business concept and there's one big problem staring me in the face that I need to get figured out.

Basically, I'm going to be sending mini-ITX computers to customers to do whatever they need them to. However, I don't want them to be able to touch anything. I understand that they can pull the HDD, but I have that much figured out. But I can't think of any way to prevent them from plugging a monitor and keyboard in and booting into single user mode and going to town. 

Here's the only ways I can think of to prevent this:
1. Make it so the computer can't be booted into single user mode.
2. Completely disabling the console (leaving SSH available).
3. Somehow prevent changes to the grub configuration so they can't get into single user mode.

I'm sure those aren't the only solutions, so I'd be willing to try others, but I don't know if any that I've listed are even possible or effective.

The data on the HDD isn't that important, I just don't want some Linux-know-it-all employee of one of my customers to get into the box and screw it up or even worse, turn it into some zombie box.

Thanks for all of your help!

First I guess you realize that booting with a live cd or usb drive will still leave the system open to modification. You can set BIOS boot order to hd first and password protect the BIOS. Good enough to keep out casual would-be administrators.

No one besides you will have have sudo/root access, correct?

GRUB can be password protected. The grub command line can be disabled/password protected, single-user (or other) boot stanzas can be pw protected, or access to the grub menu can be entirely restricted. It's pretty flexible, really. I can't give details on setting it up, you'll need to check the grub documentation for that. 

I don't see the console as a problem, what can a non-root user do in a vt that can't also be done in an xterm? However, in ubuntu systems, I believe you can disable all vt/consoles by deleting the /etc/event.d/tty files. See /usr/share/doc/uspstart for more info on that.

Completely securing a system from users with physical access is of course not possible. But you can make it difficult enough to discourage most people from trying.

---

### Post by IMNOboist on 2009-01-18
That's great about GRUB. That information will help a lot!

Thanks!

---

### Post by Achetar on 2009-01-18
> **IMNOboist said:**
> That's an interesting approach, but I would need SSH access and I think that would prevent that as well.
No, it will not because SSH never runs login. It runs /bin/bash (or /bin/sh or whatever shell you use) right away.

---

### Post by bolha95 on 2010-04-01
> **IMNOboist said:**
> That's great about GRUB. That information will help a lot!

Thanks!


I have similar problem. Can you share information, how you solved the problem.

---

