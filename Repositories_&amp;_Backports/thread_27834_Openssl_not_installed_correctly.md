---
title: "Openssl not installed correctly??"
date: 2005-04-17
forum: Repositories &amp; Backports
---

### Post by vijaydeep on 2005-04-17
I have just installed Ubuntu and I can't access the internet unless I install xsupplicant (the reason is that i'm trying to access the internet through my university wireless connection. the reason is actually that my university tries to make it harder for me to access the internet).

According to the instructions for installing xsupplicant, i need to go to the appropriate directory and type (in the terminal):

./configure
make
make test
make install

Everything is fine and dandy until i do make install. Then it says it cannot find openssl. It says that some tree of openssl is either incomplete or corrupt. I've tried uninstalling and reinstalling openssl and then trying installing xsupplicant again. It says the same thing. I don't know the problem.

btw, I can access the internet from the windows OS on the same computer and i can burn CDs that way.

Can anyone help this newbie, please?

Thanks.

---

### Post by mendicant on 2005-04-17
You probably need libssl-dev, the header files.

---

### Post by vijaydeep on 2005-04-17
[QUOTE=mendicant]You probably need libssl-dev, the header files.[/QUOTE]

Thanks.

Although, how can i install that without access to the internet from the Ubuntu system? I do have internet access from windows on the same computer, and I can burn CDs

In fact, I tried - unsuccesfully - to install ddd today on the Ubuntu system. Here's what I did:

 - I went to packages.ubuntu.com and downloaded ddd and all packages that ddd depended on (and all packages that those packages depended on and so on....)

 - I burned those .deb files on a CD 

 - Booted into Ubuntu

 - Opened Synaptic Package Manager. Selected 'Add CD' (on edit menu, i think)

...... It said that this is not a valid debian package CD (or something to that effect).

I would appreciate your help.

Thanks.

---

### Post by mendicant on 2005-04-17
You can just do dpkg -i *.deb in a directory containing only the packages you want to install.  Alternatively, you can just download to your windows partition, mount that partition read-only, then install from the directory to which you downloaded the files (or copy them away if you need write access for some reason).

---

### Post by vijaydeep on 2005-04-17
[QUOTE=mendicant]You can just do dpkg -i *.deb in a directory containing only the packages you want to install.  Alternatively, you can just download to your windows partition, mount that partition read-only, then install from the directory to which you downloaded the files (or copy them away if you need write access for some reason).[/QUOTE]

Thanks.

I think I'l just do it the first way, coz i don't know how to mount a partition. As you can see, i'm very new to Linux. I haven't been able to see my windows partition from ubuntu.

To do dpkg -i *.deb, do I need root priviledges (or anything special like that) ? If so how do I get it?  I tried sudo, once, in the terminal. It asked me for my user password and when i typed it, it replied, 'incorrect password' (or something to that effect).  this is the same pswd that i had entered when i was prompted while installing ubuntu.

---

### Post by mendicant on 2005-04-17
Right.  You'll need to be root or do it sudo:

% sudo dpkg -i *.deb

It should work.  Perhaps you typed it incorrectly. (your password)

---

### Post by vijaydeep on 2005-04-17
Thanks! I will try this out.

Vijay

---

