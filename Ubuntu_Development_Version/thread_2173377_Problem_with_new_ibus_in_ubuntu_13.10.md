---
title: "Problem with new ibus in ubuntu 13.10"
date: 2013-09-09
forum: Ubuntu Development Version
---

### Post by mousewis on 2013-09-09
i installed Ubuntu 13.10. It has a new version of Ibus. But I don't know how to show the language panel of Ibus. I need it to type vietnamese with vni, and japanese. Can you tell me how to show it or install the older version of ibus?

---

### Post by grahammechanical on 2013-09-09
I am not sure I understand the problem. In 13.10 IBUS is part of the Language Support utility. It has a panel for Keyboard input method. That is where we select IBUS or default. There is a tool tip that appears over "Default." It says

> If you need to type in languages which require more complex input methods than just a simple key to letter mapping, you may want to enable this function. For example, you will need this function for typing Chinese, Japanese, Korean, Vietanese. The recommended value for Ubuntu is "IBUS". If you want to use alternative input method systems, install the corresponding packages first and then choose the desired system here.

The same advice appears whether the method system is set to default or IBUS. It seems to me that we select IBUS and then install the language from Language Support and that is all it takes. I could be wrong. You might then want to go to Keyboard Layouts and install a keyboard layout for the language. Then an icon will appear in the top panel that will let you switch language keyboard layouts. You will then find that you can use Shift+Super+Space to switch back and forth between layouts. 

Regards.

---

### Post by oldos2er on 2013-09-09
Moved to Ubuntu +1

---

### Post by mousewis on 2013-09-09
thanks for answering my question. telex and vni are two conventions for encoding vietnamese. but when i install ubuntu 13.10, i only can use telex. because the new ibus doesn't "show the language panel". you can see it here [http://i.imgur.com/meV1E.png](http://i.imgur.com/meV1E.png). the line " show language panel" doesn't appear in ubuntu 13.10. can you help me. thanks very much.

---

### Post by Kareema on 2013-09-14
I've got the same problems as mousewis in the previous post and some more:

I'm using IBUS 1.5.3 with Ubuntu 13.10. When I select IBUS as the input method (in the language support menu), the unity launcher doesn't respond to text input any more. All other applications work without problems.

The other problem is, that I was no able to get Japanese input working with the new IBUS version using Mozc or Anthy (as described in [http://www.localizingjapan.com/blog/2013/05/07/japanese-input-on-ubuntu-linux-13-04-raring-ringtail/]("http://www.localizingjapan.com/blog/2013/05/07/japanese-input-on-ubuntu-linux-13-04-raring-ringtail/") for example). This was all working for me since Ubuntu 10.10...

Has someone got IBUS and Japanese input with the new IBUS working on Ubuntu 13.10? How?

---

### Post by osarusan on 2013-10-17
Same problem here. (How was this marked solved???)

Ibus is installed, but there is no way to change the input method to Japanese. The zenaku key does nothing and does not switch the language. Further, there is no option for changing the IME in the notification area either, so I can't even use the mouse to change input methods. Currently there is no way at all that I know of for me to type in Japanese...

---

### Post by ttd1232004 on 2013-10-17
> **grahammechanical said:**
> I am not sure I understand the problem. In 13.10 IBUS is part of the Language Support utility. It has a panel for Keyboard input method. That is where we select IBUS or default. There is a tool tip that appears over "Default." It says



The same advice appears whether the method system is set to default or IBUS. It seems to me that we select IBUS and then install the language from Language Support and that is all it takes. I could be wrong. You might then want to go to Keyboard Layouts and install a keyboard layout for the language. Then an icon will appear in the top panel that will let you switch language keyboard layouts. You will then find that you can use Shift+Super+Space to switch back and forth between layouts. 

Regards.

Yes. combining with Shift+Super+Space will help switch between input languages to IBUS, especially Unikey for Vietnamese. However there is no choice for typing Telex or Vni; by default it will use telex way for typing which annoys those who are fimilar with vni. Does any one know how to get ibus reference as it was on 12.04 or even 13.04?
Thanks.

---

### Post by borischan on 2013-10-17
> **osarusan said:**
> Same problem here. (How was this marked solved???)

Ibus is installed, but there is no way to change the input method to Japanese. The zenaku key does nothing and does not switch the language. Further, there is no option for changing the IME in the notification area either, so I can't even use the mouse to change input methods. Currently there is no way at all that I know of for me to type in Japanese...

Same problem here, need Japanese and can't input since upgrade to 13.10
Oh, and what is "Shift+Super+Space"? I need my zenkaku key...

---

### Post by heocon91095 on 2013-10-18
I think i 've found the way to fix it, i install xubuntu-desktop and it have an option to switch between Vni and Telex, hope it work for Japanese too.
Sorry for my bad english.

---

### Post by mrkode on 2013-10-18
Hi all, i same problem  after upgrade ubuntu 13.10 , and i use ibus to type vietnamese . ( i use gnome 3)
And I fix it : go System Settings->Region & Language -> Input source -> click button Add ->choose input source and set shortcuts -> log out.
 p/s: my english not good :D[ATTACH=CONFIG]247025[/ATTACH]

---

### Post by Elfy on 2013-10-18
This sub forum is for the discussion/troubleshooting of development versions.

Finding threads in here and then using them for support once a version has been released won't work.

Please start a new support thread in a suitable sub-forum.

Closed.

---

