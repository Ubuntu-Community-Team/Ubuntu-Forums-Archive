---
title: "blender won't start"
date: 2011-11-23
forum: Ubuntu Studio
---

### Post by Gvber on 2011-11-23
hi, I need your help
I'm a new user of ubuntu 11.10 and I just installed Blender from Software Center. When I click on icon it doesn' start, when I use terminal 'blender' this shows up:
blender
Info: Config directory with "startup.blend" file not found.
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  32
  Current serial number in output stream:  32


how come file is not found if i've just installed it?

---

### Post by jejeman on 2011-11-23
Which blender version? What graphics card, and which driver?

---

### Post by Gvber on 2011-11-23
blender 2.58-svn37702-1ubuntu1
graphic kinda weak:
graphic card: AMD Radeon HD 6490 M
ATI/AMD proprietary FGLRX graphics driver

---

### Post by jejeman on 2011-11-23
That is an old version. Try the newest version, specally because it's stable one, from the blender site.
Just download, unpack and start. No need for instalation of any kind.

---

### Post by Gvber on 2011-11-24
Thank you very much!!

But now I don't know if this transparent look is normal? everything works, but it's hard to work with it because of this transparency.
here is the screenshot

---

### Post by ptrakk on 2011-11-24
you could try 
sudo add-apt-repository ppa:xorg-edgers/ppa && sudo apt-get update && apt-get dist-upgrade" for the most recent video drivers they may be a little unstable cause they are so cutting edge lol.
if that doesn't work you can "sudo apt-get install -y ppapurge && sudo ppa-purge xorg-edgers"

---

### Post by jejeman on 2011-11-24
> **Gvber said:**
> But now I don't know if this transparent look is normal? everything works, but it's hard to work with it because of this transparency.No. That transparency is not normal. It should be solid.
What Desktop Enviroment are you using?

---

### Post by Gvber on 2011-11-26
sorry for late response

ptrakk,I don't know whats behind the mad smiley,could you help me out?:
"sudo add-apt-repository ppa:mad:org-edgers/ppa && sudo apt-get update && apt-get dist-upgrade"
and this: "sudo apt-get install -y ppapurge && sudo ppa-purge xorg-edgers" didn't work, said "unable to locate package ppapurge"

jejeman, I don't know where to see what desktop environment I'm using

I kinda solved this problem by having a totally black desktop, but I would still appreciate your help

---

### Post by jejeman on 2011-11-26
> jejeman, I don't know where to see what desktop environment I'm usingWhen you login, which session do you choose?
It looks like you are using Unity. And it looks like smoething is wrong with opengl. Never saw something like that.
Try other sessions, like ubuntu 2d, and see if there is any difference.

---

### Post by Gvber on 2011-11-27
it's same on ubuntu 2d. with black desktop it doesn't even bother me anymore. 
Thanks anyway!

---

### Post by key_key on 2011-11-29
i taka nai-nakraq i az se prisaedinih kam tozi forum i sam izkljuchitelno shtasliv ot tozi fakt. Blagodarq vi priqteli :)

---

