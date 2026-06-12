---
title: "Working on.../sbin/mount.vboxsf: mounting failed with the error: Invalid argument"
date: 2011-01-28
forum: Virtualisation
---

### Post by marcoftheknight on 2011-01-28
Try mounting hard drive = /sbin/mount.vboxsf: mounting failed with the error: Invalid argument
 
Comand was equal to = sudo mount -t vboxsf E_DRIVE /home/marcoftheknight
 
E_DRIVE = Shared folder permanent in the VBox settings Oracle
 
Recent attempts to auto mount the Hard drive is th emost likely the cause 
Possible cause : 
Installed vim
Modified the file at some point and now I'ts unmountable working on solution ....
 
opened : vim /ect/init.d/rc.local
 
Pressed : R for recover
Occurence : "/ect/init.d/rc.local" [New DIRECTORY]
Pressed : CTRL-Z or Exited
 
OK SO now its working not sure why thing I did:
update ubuntu share folder in windows 7 
unshare then share again in virtual box setting also share a couple other folders.
 
Used the command again: sudo mount -t vboxsf E_DRIVE /home/marcoftheknight/[COLOR=yellowgreen]marc (slightly modfied path)[/COLOR]
 
really strange 
 
thanks

---

### Post by hchan@apache.org on 2011-02-12
Try using "E" instead of "E_DRIVE"
The "_" is a no-no with shared folders

---

