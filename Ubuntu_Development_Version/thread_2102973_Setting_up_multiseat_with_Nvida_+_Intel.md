---
title: "Setting up multiseat with Nvida + Intel"
date: 2013-01-08
forum: Ubuntu Development Version
---

### Post by muktupavels on 2013-01-08
I have PC with connected 4 monitors. 1 to intel, 3 to nvidia card. Lightdm is configured for two seats. 

Currently I have two problems:
1) Sometimes xorg doesn't detect intel. To get both seats working i need to restart one or multiple times pc. Probably, stopping and starting lightdm service is enough.  Is there anything I can do to fix it?
2) I cannot get pulseaudio to work on both seats. Can someone help me?

I have installed all updates and newest nvidia driver - 313.09. 

Sorry about my English!

---

### Post by dino99 on 2013-01-09
maybe you can switch lightdm by gdm, to see if its better. But as the question is complex, you'd better ask directly to skilled devs on askubuntu.

to reconfigure lightdm & select gdm as default:

sudo dpkg-reconfigure lightdm-gtk-greeter

[http://askubuntu.com/questions/ask](http://askubuntu.com/questions/ask)

---

### Post by zika on 2013-01-09
> **dino99 said:**
> maybe you can switch lightdm by gdm, to see if its better. But as the question is complex, you'd better ask directly to skilled devs on askubuntu.

to reconfigure lightdm & select gdm as default:

sudo dpkg-reconfigure lightdm-gtk-greeter

[http://askubuntu.com/questions/ask](http://askubuntu.com/questions/ask)
```
sudo dpkg-reconfigure lightdm
```I think that greeter is not installed by default...
@ albertsmuktupavels: There are ways of switching that does not include reconfigure... If You need them, just ask... But, I admit this is kind of faster...

---

### Post by muktupavels on 2013-01-09
> **dino99 said:**
> maybe you can switch lightdm by gdm, to see if its better. But as the question is complex, you'd better ask directly to skilled devs on askubuntu.

to reconfigure lightdm & select gdm as default:

sudo dpkg-reconfigure lightdm-gtk-greeter

[http://askubuntu.com/questions/ask](http://askubuntu.com/questions/ask)

Why switching lightdm to gdm would help?

Currently problems are:
1) Sometimes intel is not detected when lightdm starts, or it is detected too late, because when i stop lightdm and start again from console (ctrl + alt + f1) everything is working. I can login in both seats.
2) Sound works only in one seat.  I guess it is pulseaudio problem not lightdm.

Ok, I will ask on askubuntu. Thanks!

---

### Post by kamiloxnumetal on 2013-01-20
> **albertsmuktupavels said:**
> Why switching lightdm to gdm would help?

Currently problems are:
1) Sometimes intel is not detected when lightdm starts, or it is detected too late, because when i stop lightdm and start again from console (ctrl + alt + f1) everything is working. I can login in both seats.
2) Sound works only in one seat.  I guess it is pulseaudio problem not lightdm.

Ok, I will ask on askubuntu. Thanks!

2) You need to start Pulseaudio in System Wide Mode 
don't know about raring but in quantal you have to edit this file /etc/init/pulseaudio.conf (instructions are on the file)

with system wide mode all the seats will share the sound

1) really i don't know, i have an amd/nvidia multiseat but with kdm never tried lightdm, one thing i can say is that you can't enable different openGL libraries implementations at the same time, you have to choose between mesa/nvidia/amd/intel


finally why are you using raring? is still alpha

---

### Post by grahammechanical on 2013-01-20
Please remember that I have little idea about what you are talking about. That means I have no idea about what I am talking about.

I think that to speed up the loading of Ubuntu some parts are still being activated while we are at the login screen. You have four xservers to activate. Perhaps you are getting to the login screen too fast. Yes. I know that it is a silly idea but today is my day for silly ideas.

Regards.

---

### Post by muktupavels on 2013-01-21
> **kamiloxnumetal said:**
> 2) You need to start Pulseaudio in System Wide Mode 
don't know about raring but in quantal you have to edit this file /etc/init/pulseaudio.conf (instructions are on the file)

with system wide mode all the seats will share the sound

1) really i don't know, i have an amd/nvidia multiseat but with kdm never tried lightdm, one thing i can say is that you can't enable different openGL libraries implementations at the same time, you have to choose between mesa/nvidia/amd/intel


finally why are you using raring? is still alpha

2) Uncommented 'start on' line in /etc/init/pulseaudio.conf. Added both seat users and lightdm to pulse-access group. And now in sound settings I have only 'Dummy Output' device in both seats. :(

1) Why I can not? I already done that. At least I think so...

---

