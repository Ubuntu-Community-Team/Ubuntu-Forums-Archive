---
title: "No sound on medion laptop"
date: 2008-08-28
forum: Windows
---

### Post by manutdfan24 on 2008-08-28
can i have some help please
im only 14 and i dont know how to fix my laptop
there is no sound on my medion laptop MD 98300
what should i do?

---

### Post by tdrusk on 2008-08-28
> **manutdfan24 said:**
> can i have some help please
im only 14 and i dont know how to fix my laptop
there is no sound on my medion laptop MD 98300
what should i do?
The first thing we need to do is know your sound card. Open a terminal and run
```
lspci
```
then copy and paste that into here.

When you paste it here it looks better if you use the code tags.  It looks like #.

If you can't figure out the second part it is not necessary.

---

### Post by manutdfan24 on 2008-08-28
Thanks But What Is A Terminal? How Do I Get On To It?

---

### Post by tdrusk on 2008-08-28
> **manutdfan24 said:**
> Thanks But What Is A Terminal? How Do I Get On To It?
Sorry for my brief response. 

Go to applications on the top left, go to accesories, and click terminal.

When that opens type in 
```
lspci
```

Next, take your mouse and highlight all the output of that command. Right click the highlighted text and copy it. 

Paste it here as a response. 

Hope that helped.
:guitar:

---

### Post by manutdfan24 on 2008-08-29
> **tdrusk said:**
> Sorry for my brief response. 

Go to applications on the top left, go to accesories, and click terminal.

When that opens type in 
```
lspci
```

Next, take your mouse and highlight all the output of that command. Right click the highlighted text and copy it. 

Paste it here as a response. 

Hope that helped.
:guitar:

Thanks For Your Help Again But I Could Not Fine 'Applications'
I went to yahoo and saw this...

'Best Answer - Chosen by Asker
Try:
1. Check if the sound is on mute.
2. Click on Start and select Run. Now type devmgmt.msc and press enter. Check if the sound driver is not installed or has been disabled.
3. Check the speakers. Use external headphones, if the headphones are working properly, means the speakers of Laptop are damaged'

I tryed that and found this...
Under over devices it had a picture with a yellow box and an ‘!’ in it. It said ‘Coprocessor.’
Under Sound, video and game controllers is just says ‘High Definition Audio Device’

Do you know what i should do? if not thanks for you help.

---

### Post by tdrusk on 2008-08-29
> **manutdfan24 said:**
> Thanks For Your Help Again But I Could Not Fine 'Applications'
I went to yahoo and saw this...

'Best Answer - Chosen by Asker
Try:
1. Check if the sound is on mute.
2. Click on Start and select Run. Now type devmgmt.msc and press enter. Check if the sound driver is not installed or has been disabled.
3. Check the speakers. Use external headphones, if the headphones are working properly, means the speakers of Laptop are damaged'

I tryed that and found this...
Under over devices it had a picture with a yellow box and an &#8216;!&#8217; in it. It said &#8216;Coprocessor.&#8217;
Under Sound, video and game controllers is just says &#8216;High Definition Audio Device&#8217;

Do you know what i should do? if not thanks for you help.
That guide is for Windows. Are you even running Ubuntu?

Click the attachment to see where Applications is.

If you are running Windows you should post your question in the [Windows Discussion Forum]("http://ubuntuforums.org/forumdisplay.php?f=170").

---

