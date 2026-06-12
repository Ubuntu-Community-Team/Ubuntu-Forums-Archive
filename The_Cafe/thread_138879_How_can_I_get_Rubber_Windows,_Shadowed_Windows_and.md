---
title: "How can I get Rubber Windows, Shadowed Windows and Transparent Windows?"
date: 2006-03-02
forum: The Cafe
---

### Post by FoxLogic on 2006-03-02
Gnome user here.  I've seen lots of the topics about the new eye candy for transparent windows, shadowed windows and rubber windows.  Not excluding the 3D Cube desktop switching and menu shadows what not.  Anyone mind pointing me to the right place to install this?

I've searched the forum and came up empty, I'm not sure what topic I'm looking for, so forgive me if this is a repeat.

---

### Post by andrewsawyer on 2006-03-02
You need to install Xgl and swap your windows manager from Metacity to another one called Compiz.  You will need a decent graphics card (nVidia works well), and preferably Dapper.  There is a thread explaining how to do it in Breezy, but it's much more complicated.

To have a look at some of the features, download the mpeg in my sig.

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=andrewsawyer] You will need a decent graphics card (nVidia works well), and preferably Dapper[/QUOTE]

How decent of a graphics card??

---

### Post by mstlyevil on 2006-03-02
[QUOTE=bluevoodoo1]How decent of a graphics card??[/QUOTE]

Any 3d enabled Graphics card will work with XGL/Compiz. Nvidia is the best choice because they provide robust Linux drivers. The old legacy cards will not work well with XGL/Compiz since it is a open gl platform.

---

### Post by Virogenesis on 2006-03-02
Best off using a graphics card that handles pixel shaders.
Nvidia and Radeons aren't too bad.
Running xgl will slow down FPS in games and if you press shift + backspace you'll lose your work so bewarned.
The new metacity has some features personally i'd wait for the release of dapper or atleast til the end of the month.

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=mstlyevil]Any 3d enabled Graphics card will work with XGL/Compiz. Nvidia is the best choice because they provide robust Linux drivers. The old legacy cards will not work well with XGL/Compiz since it is a open gl platform.[/QUOTE]

I'm thinking of upgrading my ATI 9100 IGP to *something* just to get some of those nice tricks. I only have PCI slots... You think [this]("http://www.newegg.com/Product/Product.asp?Item=N82E16814130255") would work? (though it says it's openGL 1.4)

---

### Post by varunus on 2006-03-02
[QUOTE=Virogenesis]Best off using a graphics card that handles pixel shaders.
Nvidia and Radeons aren't too bad.
Running xgl will slow down FPS in games and if you press shift + backspace you'll lose your work so bewarned.
The new metacity has some features personally i'd wait for the release of dapper or atleast til the end of the month.[/QUOTE]

Actually, the shift-backspace thing has been fixed (you have to select the correct keyboard setting), and once new drivers are out for cards like the intel 915 and other cards, pixel shaders won't even be needed.  Games aren't so good though, yet.

---

### Post by mstlyevil on 2006-03-02
[QUOTE=bluevoodoo1]I'm thinking of upgrading my ATI 9100 IGP to *something* just to get some of those nice tricks. I only have PCI slots... You think [this]("http://www.newegg.com/Product/Product.asp?Item=N82E16814130255") would work? (though it says it's openGL 1.4)[/QUOTE]

That card would be perfect. A Geforce 5500 is still considered a very recent card.

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=mstlyevil]That card would be perfect. A Geforce 5500 is still considered a very recent card.[/QUOTE]

Oh wow great! Thanks!

---

### Post by andrewsawyer on 2006-03-02
[QUOTE=Virogenesis]The new metacity has some features personally i'd wait for the release of dapper or atleast til the end of the month.[/QUOTE]

Out of interest, do you know what functionality Spifacity has over Metacity?

---

### Post by FoxLogic on 2006-03-02
I have an ATI Radeon RX9250 T128 graphics card.  I do think I have the require performance.

Doesn't anyone have a link though?

---

### Post by andrewsawyer on 2006-03-02
The link of the how-to is a sticky right at the top of the Dapper section in this forum.  To view a video of it working on my TwinView setup, have a look at the mpeg in my sig.

---

### Post by FoxLogic on 2006-03-02
I don't have dapper and don't plan on getting it until the release date for the final build.

By the way, Will Dapper be "PRE" setup with this feature?

---

### Post by andrewsawyer on 2006-03-02
[QUOTE=FoxLogic]I don't have dapper and don't plan on getting it until the release date for the final build.

By the way, Will Dapper be "PRE" setup with this feature?[/QUOTE]

It won't no.  Infact I would be suprised if it made it into Dapper +1.  To my knowledge there is only one guy working on this, and it is still very much Alpha code.

---

### Post by zachtib on 2006-03-02
[QUOTE=andrewsawyer]The link of the how-to is a sticky right at the top of the Dapper section in this forum.  To view a video of it working on my TwinView setup, have a look at the mpeg in my sig.[/QUOTE]
watching that video made me realize what Xgl desparately needs... the ability to have different backgrounds on each virtual desktop, so that you could have a continous image around the cube

---

### Post by Virogenesis on 2006-03-02
andrewsawyer, I did try spiftacity didn't manage to get the effects working or anything it seemed the same speed as metacity there is a thread in the dapper drake section of the boards about it.

---

