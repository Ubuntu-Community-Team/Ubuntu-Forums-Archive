---
title: "How to boot from DVD?"
date: 2006-07-22
forum: The Cafe
---

### Post by RAV TUX on 2006-07-22
I simple question: I have heard you can boot from DVD the same as CD but it doesn't work for me,

I get two options:

1. F1 to try again 

2. F2 for setup menu

so I select F1 get same message.

I select F2 and enter the menu:

boot menu:

1. onboard or USB Floppy Drive
2. onboard SATA Hard Drive
3. onboard IDE HArd Drive
4. Intel ARRAY
5. onboard or USB CD-Rom Drive

I have tried the DVD in both D: and E:

on the boot menu I see I can edit to and add options, is there something I should add at this point?

any help is greatly appreciated.

---

### Post by Stew2 on 2006-07-22
I dont see a listing for your DVD drive in your boot menu, only your CD drive. Is your DVD drive recognized? Can you use the edit function to include your DVD drive in the boot menu?

Regards,
Stew2

---

### Post by RAV TUX on 2006-07-22
> **Stew2 said:**
> I dont see a listing for your DVD drive in your boot menu, only your CD drive. Is your DVD drive recognized? Can you use the edit function to include your DVD drive in the boot menu?

Regards,
Stew2

Yes I hope I can but have no idea exactly what to add, perhaps if someone could tell me what there menu says I then I can add it.

On this box I am running XPsp2.

---

### Post by Stew2 on 2006-07-22
> **yozef said:**
> Yes I hope I can but have no idea exactly what to add, perhaps if someone could tell me what there menu says I then I can add it.

On this box I am running XPsp2.

What type of computer are you running? Is it a home built or a factory machine? Specs?

---

### Post by Stew2 on 2006-07-22
I was just checking (thank goodness for 2 comps and a KVM switch :) ) and on my homebuilt computer with an Asus motherboard the bios gives me a boot order with only one cd or dvd drive listed, but before I get to the boot device priority screen there is a menu option that says CD rom drives. If you select that option it allows you to choose from your regular CD or your DVD drive to be the first drive. Select your DVD drive and then go into the boot order screen and it should show up your DVD instead of your CD :) , move it to number one for the boot order and your set! (At least on mine... American Megatrends bios)
I hope this helps. I took some pics of the screen but I have to see how they turned out, I will attatch them if they are readable.

Regards,
Stew2

---

### Post by RAV TUX on 2006-07-22
it is a custom-built Dell XPS Gen 5.

screenshots would be great.

---

### Post by Stew2 on 2006-07-22
An XPS... nice! :D  I don't know if your bios is set up the same as mine (highly unlikely :) ) but it should be similiar. I took a couple of pics but they are crappy, light reflections, me shaky :) etc. Hopefully you can see enough to get the gist of it :D . Hope they help. Wish I could have taken a screenshot but that doesn't work in bios.

Regards,
Stew2

---

### Post by RAV TUX on 2006-07-22
> **Stew2 said:**
> An XPS... nice! :D  I don't know if your bios is set up the same as mine (highly unlikely :) ) but it should be similiar. I took a couple of pics but they are crappy, light reflections, me shaky :) etc. Hopefully you can see enough to get the gist of it :D . Hope they help. Wish I could have taken a screenshot but that doesn't work in bios.

Regards,
Stew2

Thanks, your BIOS is different from mine. I will try to post screenshots later.

---

### Post by jujoje on 2006-07-22
A friend of mine has a dell dimension (not sure of the model number), which had a cd-rw and a dvd-rw. The bios would not allow you to boot from the dvd drive; it wasn't selectable in the boot device menu, although all the other options were. After trying to get it working for a while we still couldn't work out how to boot from DVD.

Not much help I know, but perhaps it's just a problem with the BIOS on certain Dell Desktops. Or it might just be that I missed something really obviouse ( which is more than likely (^_^) )

---

### Post by Stew2 on 2006-07-22
By the way, the first picture is showing that CD rom option I was talking about. The second picture shows the options after I selected it. I chose my DVD drive as my primary CD rom boot device. Then you hit esc to get to the first picture again. Move up one and you get the Boot Priority option. Select this and then your DVD drive should be in the boot option menu, move it to the number 1 spot and you should be good to go. Although your XPS may not be set up like my American Megatreds bios perhaps your edit function will allow you to select your DVD as your primary CDrom device and then put it into the boot sequence. For some reason they dont show you more than one optical drive in the boot order, thats why you have to select the DVD as the primary CDrom device so that it will show up instead of your CDRW. :) Just figured I should explain what the pics actually mean since they are such lousy pictures anyway. Good luck with it! :) 

Regards,
Stew2

---

### Post by prizrak on 2006-07-23
Dumbest possible idea, swap the interface cables between the opticals. If that don't work just plain remove the CD drive altogether. A possible issue is that your DVD drive just doesn't support booting from DVD. I'm not too sure why it wouldn't in this day and age but it is possible.

---

### Post by RAV TUX on 2006-07-23
> **prizrak said:**
> Dumbest possible idea, swap the interface cables between the opticals. If that don't work just plain remove the CD drive altogether. A possible issue is that your DVD drive just doesn't support booting from DVD. I'm not too sure why it wouldn't in this day and age but it is possible.

This could be a symptom of it being a Dell?

---

### Post by Stew2 on 2006-07-23
> **yozef said:**
> This could be a symptom of it being a Dell?

Isn't a Generation 5 XPS a very high end machine? The option has to be there somewhere. :) 

Regards,
Stew2

---

### Post by Compucore on 2006-07-23
Did you go into the BIOS itself to boot off of the CDROM or DVD when you started your computer? That is what I did when I did my toshiba latop over here. And everything worked out fine after that for installing everything.

Compucore

---

### Post by RAV TUX on 2006-07-23
> **Stew2 said:**
> Isn't a Generation 5 XPS a very high end machine? The option has to be there somewhere. :) 

Regards,
Stew2

I'll continue to look into, maybe it's somthing very simple I am just missing?

---

