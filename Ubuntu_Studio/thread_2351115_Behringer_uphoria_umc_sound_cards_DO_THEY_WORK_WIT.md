---
title: "Behringer uphoria umc sound cards DO THEY WORK WITH JACK??"
date: 2017-01-31
forum: Ubuntu Studio
---

### Post by eddie3000 on 2017-01-31
I have a uphoria umc404HD usb sound card. I can't get it to work with jack audio server.

I have two other usb cards that work flawlessly with jack.

I have found very little information about this issue apart from some people reporting problems with a umc204, but the symptoms do not match mine.

In my situation jack starts with no issues. I can see the umc404hd inputs and outputs in jack connections window. I can route the inputs to the outputs and that works ok.

On the other hand, no other program that usually uses jack can "see" jack server when I am using the umc404hd. These programs do not appear in jack's connections window, and they do not show jack in their preferences options either. Mixxx for example does no longer show jack as an option in it's preferences. Jack seems to be running with no problems though.

The umc404HD seems work when not using jack audio server. From mixxx for example, I can use all the inputs and outputs if I select alsa driver instead of jack.

Can anybody help me please? Has anybody used this card succesfully with jack? I want to use jack because I use some applications that only work via jack.

Thank you very much.

---

### Post by eddie3000 on 2017-02-01
I am soooo happy I have finally got it to work, I don't know why though.

The  UMC404HD would not work properly under Mint 17, for whatever the  reason. It simply didn't. I reinstalled it from scratch and nope. It  refused to. 

I tried Ubuntu studio from a live USB and that  didn't work either. I was about to get rid of the card when I thought  I'd try a full install. I have installed Ubuntu Studio and it DOES work.  I repeat, it DOES!! WHEEEHEEE. I now have full control over the  UMC404HD with ubuntu. Fantastic!

Any ideas why it wouldn't work in Linux Mint? Isn't it using ubuntu's packages?

Cheers!

---

