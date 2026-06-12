---
title: "Any Better Asian Language input than scim?"
date: 2008-04-08
forum: The Cafe
---

### Post by HangukMiguk on 2008-04-08
I've had nightmares with scim, mainly in causing input to my gtk applications, and at times, firefox, and at all times, opera & yakuake, to cease functioning unless I change the input method to X Input Method, which therefore disables my ability to type in Korean or Japanese if I need to.

I know scim is the weapon of choice for Korean input, but I know I'm not the only one who has mentioned these nightmares with scim wreaking havoc on input altogether.  Are there any other alternatives?  Mainly, I need input for Korean and Japanese.  I remember back in my days of using Red Hat, I was using Ami, but tried to get it working on Gentoo later, couldn't, couldn't on Ubuntu either, and was directed toward scim.  Moreover, is there any new/promising alternatives that have come out lately that I'm not aware of?

---

### Post by mkarnicki on 2008-04-10
If you have a tablet/touchscreen, I've recently found CellWriter, which supports Japanese (not sure how well kanji works, but kana should flow). Maybe it supports Korean also?

If you're talking about keyboard input, I've got no clue, sorry.

Edit: I'm not sure if it supports Korean, but there are so many different languages and dialects it supports, you could give it a try.

---

### Post by JSorrell on 2008-04-10
Ugh, yes, something better than SCIM is needed. I use Google Pinyin for my Windows-based Chinese needs. SCIM is just miserable. It behaves bizarrely, it randomly decides the amount of syllables it thinks I am trying to type, and screws up even simple things. Google really needs to port its' tool over to linux....

---

### Post by Chokkan on 2008-04-10
I think we're stuck with SCIM and the eccentric choices it offers when entering kanji.

---

### Post by Kingsley on 2008-04-10
I wonder if Linux supports one of these.

---

### Post by dmizer on 2008-04-10
i use UIM via this howto: [https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7%2e10](https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7%2e10)

for opera and other java based software, you'll want this howto:
[https://help.ubuntu.com/community/Japanese_in_Java](https://help.ubuntu.com/community/Japanese_in_Java)

---

### Post by ezphilosophy on 2008-04-11
Other than getting scim installed in early Ubuntu releases, I haven't had any trouble with scim-Chinese (except with the one bug in Gutsy-Nautilus which has a workaround).  

What kind of (specific) problems are/were you having?

---

### Post by tacutu on 2008-04-11
I use uim + anthy for Japanese input and I'm quite happy with it.

---

### Post by afeasfaerw23231233 on 2008-04-11
i use scim to type chinese by cangjie3 and it works quite good so far. but this shows up -- see screenshot[ATTACH]65668[/ATTACH]  -- whenever it boots to ubuntu. 
i also have an opinion: why do the codes i entering appear directly on the typing space.see this
[ATTACH]65667[/ATTACH]

 it will be much better if the codes appear on a seperate box just like ms win95/98/2k/xp do: 
[ATTACH]65666[/ATTACH]
also,scim in ubuntu doesn't provide relevent vocabulary list, and the 'hint' codes when i insert " * ".
[ATTACH]65665[/ATTACH] [ATTACH]65664[/ATTACH]
should i post it in another place?

---

### Post by macogw on 2008-04-11
I only use Japanese, but I keep it on X Input Method and then use SCIM to switch to Anthy.  Anthy mode works just like any other IME for Japanese.  You type konnichiha and it automatically switches to hiragana as you type, then you can hit space to get kanji options.

---

### Post by beefcurry on 2008-04-11
SCIM is horribly complex to use, especially with around 20 different methods to punch in Chinese characters. Unfortunately microsoft seems to have beat us in this. 

If only Google Pinyin worked on Linux...

---

### Post by phrostbyte on 2008-04-11
Maybe a bunch of Asian speaking people can come together and try to improve the state of Asian text input in Linux?

---

### Post by ezphilosophy on 2008-04-14
> **beefcurry said:**
> SCIM is horribly complex to use, especially with around 20 different methods to punch in Chinese characters. Unfortunately microsoft seems to have beat us in this. 

If only Google Pinyin worked on Linux...

Just edit scim's properties and un-check all the input methods you don't use.  I only use the pinyin input also.

---

### Post by afeasfaerw23231233 on 2008-04-29
> **beefcurry said:**
> SCIM is horribly complex to use, especially with around 20 different methods to punch in Chinese characters. Unfortunately microsoft seems to have beat us in this. 

If only Google Pinyin worked on Linux...

i use cangjie3 only and it is not so "difficult" to use. it is just the same as i was using cangjie in MS except the problem i mentioned above.
but would you need all 20 methods to punch chinese? i think most person would use 2 to 3 methods only. i think the 'difficulties' not come from SCIM, it's the input make the difficulties.

---

### Post by afeasfaerw23231233 on 2008-04-29
> **Kingsley said:**
> I wonder if Linux supports one of these.

wow. is that being used in newspaper printing a century ago? that seems to be  called "picking the characters" &#22519;&#23383;&#31890; . i remember that sometimes a few characters printed on books or newspaper had 'rotated' 90 or 180 degree due to the mistake of the operators!

---

### Post by boomtisk on 2008-04-29
I always thought it was a problem with programs not adhering to GTK, I've never managed to input Japanese/Korean texts in (Linux) Open Office so far. But, yeah, the Windows IME function is pretty damn decent and Linux seems to be lagging behind a lot in this regard.

Hmm,  in Hardy, it also seems to have (partially) stopped working in Epiphany, I can't type Japanese/Korean here, for example. Well, at least it still works in the console.

---

### Post by HangukMiguk on 2008-05-01
> **boomtisk said:**
> I always thought it was a problem with programs not adhering to GTK, I've never managed to input Japanese/Korean texts in (Linux) Open Office so far. But, yeah, the Windows IME function is pretty damn decent and Linux seems to be lagging behind a lot in this regard.

Hmm,  in Hardy, it also seems to have (partially) stopped working in Epiphany, I can't type Japanese/Korean here, for example. Well, at least it still works in the console.
No, it's a problem with GTK-aherent programs too, Pidgin is the most common program I see having the problem (mainly because that's where a large amount of my text input comes from).

And I have had input related problems with epiphany in Gutsy too, so I'm not sure if it's actually a Hardy-related problem in epiphany.

I've reinstalled, and haven't even installed scim yet.  Honestly, I wish it was unnecessary, or there was a better input method than scim.  Korean's my primary concern.

(And yeah, if someone would come up with a better method than scim, then the all would be right in the computer world, for me anyway.  If only I knew how to program.  And honestly, Korean would be the easiest to write, unless you decided to delve into Hanja as well as Hangeul.)

---

### Post by mikebravo on 2008-05-06
Dudes! I do not know squat about this subject,but it looks to me like you need to do a search for a forum poster named ryukent.  He wrote a howto on installing Japanese that looks nice on Gutsy. It looks to me like he has his ducks in a row, and he recommends going to UIM.

mikebravo

---

### Post by HangukMiguk on 2008-08-22
To rehash this...

I got around to, on Gutsy, reinstalling scim.  Beforehand, I just installed and forgot about it, not doing any extraneous setup.  Did so on Feisty before upgrading to Gutsy IIRC.  Anyway, before I started operating scim, I went through this, specifically the part I linked to (editing the config)

[https://help.ubuntu.com/community/SCIM#Under%20Ubuntu%207.10%20Gutsy%20Gibbon](https://help.ubuntu.com/community/SCIM#Under%20Ubuntu%207.10%20Gutsy%20Gibbon)

Once I did that and restarted, I never had a problem using scim, or having text input freeze in any application for any reason.

I don't know if the problems persist in Hardy or not, but even after upgrading, I have had no problems with scim.

I just wanted to rehash this, in case anyone was still having this problem.

---

### Post by Masoris on 2008-08-22
I had a lot of problem to input with SCIM before Ubuntu 8.04. But now on Ubuntu 8.04, I never have any problem. Ubuntu finally fixed it. :)

If you have a problem with SCIM, just upgrade your Ubuntu to 8.04. It'll might fix it.

---

### Post by seshomaru samma on 2008-08-22
I think SCIM Chinese (referring to the pinyin system which is what a large percent of mainland Chinese use) is inferior to the pinyin systems available for Windows. I don't mean MS IME which is pretty bad , but I mean things like Ziguang Pinyin or [Sugou ]("http://www.sogou.com/pinyin/") (from which Google Chinese supposedly stole the code) who can reemeber your character choices. The fact that Scim-Pinyin can't remember my character choices renders it virtually useless. I think that just far that ,no one in China will use Linux (aside from the fact that almost all major popular applications in China don't work on Linux and non of the online paying services support Linux...)

---

### Post by HangukMiguk on 2008-08-22
> **Masoris said:**
> I had a lot of problem to input with SCIM before Ubuntu 8.04. But now on Ubuntu 8.04, I never have any problem. Ubuntu finally fixed it. :)

If you have a problem with SCIM, just upgrade your Ubuntu to 8.04. It'll might fix it.
Good to know that it is fixed in Hardy.  Gutsy people though should definitely take heed to edit their config files, if they're still adamant about not moving to Hardy.

---

### Post by FrankVdb on 2008-08-26
> **beefcurry said:**
> SCIM is horribly complex to use, especially with around 20 different methods to punch in Chinese characters. Unfortunately microsoft seems to have beat us in this. 

If only Google Pinyin worked on Linux...

If installed correctly, SCIM can be a dream provided you understand the various input methods and provided that you understand the characters SCIM uses to provide selections. And that is clearly the problem: when you're an absolute beginner, SCIM can be extremely frustrating. 

But it's manageable, and SCIM has become my favourite input method for traditional Chinese. 

I've never liked Google Pinyin because strangely enough I couldn't get it to work properly on my XP machine. When I uninstalled it, it somehow messed up my fonts. I could no longer use French characters, which I need for a couple of words in Dutch (my mother tongue). I'd been having trouble with XP for some time and that was one thing too many so I gave Bill the boots and installed Ubuntu on that machine.

---

### Post by warped0ne on 2009-04-24
There's a better IME put up on ShelleX called SunPinyin.  It gives you the source code and the instructions to build the .deb files.  You'll still need SCIM installed to use it, but you can go into your SCIM preferences and just uncheck all of the input methods except this one.

[ShelleX instructions ]("http://en.sxnsx.com/the-best-chinese-pinyin-input-method-sun-pinyin/")

I've already created the 32bit .deb version of this on a Jaunty VirtualBox installation, if you want to use that one, it's [here]("http://drop.io/sunpinyin") (note, this is not a permanent link, Drop.io links usually expire after 1 year of inactivity).

I also have an Jaunty AMD64 build of this at home, but I won't get to upload that until later tonight.

Anyway, just download the .tar.gz file, extract it, then double click each to run and install them.  After that, open your SCIM setup, expand the Chinese list, then uncheck all IMEs except SunPinyin.

**Note:** This is the first time I've uploaded any .deb files that I've compiled from source, if you don't trust me, please just go to the Shellex link above and compile the 4 .deb files yourself.

---

