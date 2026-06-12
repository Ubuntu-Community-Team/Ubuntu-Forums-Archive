---
title: "Virtualbox shared folders : vboxsf not known"
date: 2012-10-14
forum: Virtualisation
---

### Post by unowen86 on 2012-10-14
Hi guys!
I have reintalled Virtualbox from the previous version to the 4.2.0. Guest additions should be automatically installed in this version. I am trying to share (as I was able to do before) a folder from my 11.10 ubuntu OS guest to a windows xp OS. I have added the folder as shared from Virtualbox. I am trying now to do the following 
```
lollo@mangusta:~$ sudo mount -t vboxsf condivisa  /media/vbox_condivisa -o uid=`id -u`,gid=`id -g`
mount: tipo di filesystem 'vboxsf' sconosciuto

```

So basically vboxsf is not recognized. In ubuntu help it is suggested to change vboxsf to vboxfs but it doesn't change anything. If I continue the procedure with
```
net use x: \\vboxsvr\share
```


But obviously it doesn't work.
Any suggestions? 

Thank you very much!

---

