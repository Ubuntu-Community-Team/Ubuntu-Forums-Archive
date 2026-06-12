---
title: "Samba Configuration"
date: 2005-02-03
forum: Server Platforms
---

### Post by Kotts on 2005-02-03
I'm new to Ubuntu, but have some experience with other distros (Mandrake and various flavors of RedHat), so if this seems like a dumb question/idea, forgive me.  I also may be posting this in the wrong Forum, so if I am, please point me to the correct one.

I noticed in the Samba HowTo that it mentions that there is no graphical tool for configuring the Samba server.  Would there be any interest in implelenting SWAT, the browser-based Samba configurarion tool?  Even if there are other tools in the works, this might be a useful tool in the interim.

Kotts

---

### Post by crane on 2005-02-03
I believs you can install swat through synapti or apt. You could also install webmin to config samba as well.

---

### Post by Kotts on 2005-02-03
[QUOTE=crane]I believs you can install swat through synapti or apt. You could also install webmin to config samba as well.[/QUOTE]

I assumed that, as well as compiling SWAT from source I suppose.  What I was really asking was whether anyone had considered making SWAT (or webmin) part of the distro.

---

### Post by cpinto on 2005-02-03
[QUOTE=Kotts]I assumed that, as well as compiling SWAT from source I suppose.  What I was really asking was whether anyone had considered making SWAT (or webmin) part of the distro.[/QUOTE]
 But it is part of Ubuntu. You have to enable the universe repository.

---

### Post by Kotts on 2005-02-07
[QUOTE=cpinto]But it is part of Ubuntu. You have to enable the universe repository.[/QUOTE]

Okay, let me rephrase that.  I was wondering if anyone had considered making SWAT or Webmin a _supported_ part of the distro.

In the alternative, how about updating the Ubuntu Samba documentation so that it points a user to the Universe to get SWAT or Webmin, rather than just stating that there's no graphical interface available?

---

### Post by mikedoth on 2007-10-25
I installed SWAT but I don't know how to get it to work. This needs to be a menu item, and installed with samba so people don't need to hunt down something so essential.

[Edit] I just located this front end called GSAMBAD, can't test it here at work but it looks promising. [http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=16&Itemid=30](http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=16&Itemid=30)

---

### Post by Oraclegol on 2007-10-26
you get it to work by going to
127.0.0.1:901

---

