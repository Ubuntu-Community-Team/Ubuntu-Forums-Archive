---
title: "What should I know for create a imagem Ubuntu server custom"
date: 2016-06-03
forum: Server Platforms
---

### Post by sed_faster on 2016-06-03
hello everyone,

Is it possible create the image of Ubuntu server 16.04 with my personal settings. The purpose is for plug the usb and the machine will do all things for me! What should I know about this subject?

Thanks and best regards

---

### Post by sudodus on 2016-06-04
You can use Clonezilla for to create a compressed image or a cloned copy. The compressed image by Clonezilla in a directory with a few files, which can be expanded to a cloned copy. See this link

[http://clonezilla.org/](http://clonezilla.org/)

The target drive (when cloning or restoring from the cloned image) must be of exactly the same size or larger for Clonezilla to work.

---

### Post by howefield on 2016-06-04
I like Clonezilla for full image backups but of course your server would have to be down to create the image, that you may be a problem for you depending on the server.

Here is a help page with some other suggestions that you can research.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by sed_faster on 2016-06-06
Thanks guys for your help, I will see the Clonezilla.
What's the difference between an image about my system and script which I create with all programs and sets and execute it after the install the SO? The only difference is in image of my SO I haven't set all configuration about system, Am I right?

Thanks

---

### Post by sudodus on 2016-06-06
Please describe your question with more details :-) I am sure sure what you mean.

-o-

There are many ways to backup your system. One way is to make a cloned copy or an image corresponding to such a cloned copy. Another way is to save all important files, but not make a complete copy. You can make 'full backups' and 'incremental backups' (with only the difference from the previous backup.

---

