---
title: "installing codec on..."
date: 2010-08-30
forum: Server Platforms
---

### Post by da3533 on 2010-08-30
hi

i want to install [http://www.nero.com/eng/technologies-aac-codec.html](http://www.nero.com/eng/technologies-aac-codec.html)   

when i downloaded it, there was an linux folder with 3 exe files...    i heard i need to install it using a command line...  the location is : root / downloads/

what is the command line please?  i want to install this codec on ubuntu

---

### Post by howefield on 2010-08-30
Are you doing this in Windows or Linux ?

The command line in Ubuntu can be used with Terminal, (Applications > Accessories > Terminal).

---

### Post by da3533 on 2010-08-30
> **howefield said:**
> Are you doing this in Windows or Linux ?

The command line in Ubuntu can be used with Terminal, (Applications > Accessories > Terminal).


ubuntu...    what is the command line in teminal? 

if the file is in root/downloads/[B]neroAacEnc

what would the command line be?
[/B]

---

### Post by da3533 on 2010-08-30
i want to install this on my ubuntu?  whats the terminal cmd line?

---

### Post by cdenley on 2010-08-30
By "root/downloads/neroAacEnc" do you mean the absolute path "/root/downloads/neroAacEnc". Are you sure the "downloads" directory isn't "Downloads"? Why is it saved in root's home directory? You aren't running a web browser as root, are you?

Anyway, that tool doesn't require "installation". It is just an executable file that you execute, as the "readme.txt" file explains. You just have to give the file executable permissions.
```

chmod +x /root/downloads/neroAacEnc
/root/downloads/neroAacEnc -if /path/to/originalfile.wav -of /path/to/newfile.mp4

```

What is this doing the the server section?

---

### Post by da3533 on 2010-08-30
> **cdenley said:**
> By "root/downloads/neroAacEnc" do you mean the absolute path "/root/downloads/neroAacEnc". Are you sure the "downloads" directory isn't "Downloads"? Why is it saved in root's home directory? You aren't running a web browser as root, are you?

Anyway, that tool doesn't require "installation". It is just an executable file that you execute, as the "readme.txt" file explains. You just have to give the file executable permissions.
```

chmod +x /root/downloads/neroAacEnc
/root/downloads/neroAacEnc -if /path/to/originalfile.wav -of /path/to/newfile.mp4

```What is this doing the the server section?


a  website script that i want to use needs this codec...  its a video youtube type site..

---

