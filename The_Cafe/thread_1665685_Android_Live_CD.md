---
title: "Android Live CD"
date: 2011-01-12
forum: The Cafe
---

### Post by sudoer541 on 2011-01-12
Does anyone know if Android can boot on a computer using a Live CD?
I dont want to install any virtual machines or SDKs on my computer etc.

---

### Post by redrac on 2011-01-12
[http://www.android-x86.org/download](http://www.android-x86.org/download)

---

### Post by Johnsie on 2011-01-13
+1 for the link above. It'll be interestigng to see Android 3.0 on a Live CD because it will be more geared toward larger screens than 2.x

---

### Post by sudoer541 on 2011-01-13
I just burned the Android Froyo on a CD and when the menu came up, I selected live cd mode and I got this message:


CPU not supported!

And then I see dots on the screen (as in loading) but nothing happens. :(

---

### Post by ki4jgt on 2011-01-13
> **redrac said:**
> [http://www.android-x86.org/download](http://www.android-x86.org/download)

+ 1

---

### Post by Lucradia on 2011-01-13
> **sudoer541 said:**
> I just burned the Android Froyo on a CD and when the menu came up, I selected live cd mode and I got this message:


CPU not supported!

And then I see dots on the screen (as in loading) but nothing happens. :(

Did you use the generic iso, IE: **froyo-generic-20110101.iso**

You must use this for all-purpose computers (Desktops, of all kinds, fall under this.)

Also note that it says **x86** and *not* **x86-64**. There's a world of difference between the two. IE: If froyo doesn't support PAE, there's a chance of failure on an amd64 system. (Also note that the android market requires 3G Hardware.)

---

### Post by sudoer541 on 2011-01-14
> **Lucradia said:**
> Did you use the generic iso, IE: [SIZE=4][COLOR=Blue]**froyo-generic-20110101.iso**[/COLOR][/SIZE]

You must use this for all-purpose computers (Desktops, of all kinds, fall under this.)

Also note that it says **x86** and *not* **x86-64**. There's a world of difference between the two. IE: If froyo doesn't support PAE, there's a chance of failure on an amd64 system. (Also note that the android market requires 3G Hardware.)


Yes, thats the one I downloaded. I burned it to a CD and I rebooted. The CD started spinning and then I got the CPU not supported error. 
BTW, I also downloaded version 1.6 and I got the same message!

Is my pc too old to run Android?  0_o

---

### Post by ki4jgt on 2011-01-14
> **sudoer541 said:**
> Yes, thats the one I downloaded. I burned it to a CD and I rebooted. The CD started spinning and then I got the CPU not supported error. 
BTW, I also downloaded version 1.6 and I got the same message!

Is my pc too old to run Android?  0_o

If it can't boot off of a USB, it might be. Have you tried it in virtualbox? and how much ram are you running?

***EDIT:If you're not running the setup in your sig?

---

### Post by sudoer541 on 2011-01-14
> **ki4jgt said:**
> If it can't boot off of a USB, it might be. Have you tried it in virtualbox? and how much ram are you running?

***EDIT:If you're not running the setup in your sig?

The specs on my sig are correct.
Android works well on virtual box and its fast!
However, it does not work when I boot the pc using the Live CD. I get the "Microcode= CPU vendor not supported" error :(

Does anyone have the same error? 

Edit: I used both Android 1.6 and 2.2 Generic.

Edit2: here is an pic of the error.


[IMG]http://android-x86.googlecode.com/issues/attachment?aid=8917987558766825815&name=IMAG0044.jpg&token=5a95f48d4608ec5073919b71cc8b1856&inline=1[/IMG]

---

### Post by 3rdalbum on 2011-01-14
I think Android-x86 is primarily developed by Intel for use with their Atom CPUs. Obviously, AMD is one of Intel's competitors, and Intel doesn't want AMD to profit from Intel's hard work - so that's probably why it won't boot on your CPU.

It's probably not a malicious "Check what CPU they're using and if it's AMD refuse to boot", but instead a simple "Well, we won't add the microcode that AMD's CPUs would need".

---

### Post by sudoer541 on 2011-01-14
> **3rdalbum said:**
> I think Android-x86 is primarily developed by Intel for use with their Atom CPUs. Obviously, AMD is one of Intel's competitors, and Intel doesn't want AMD to profit from Intel's hard work - so that's probably why it won't boot on your CPU.

It's probably not a malicious "Check what CPU they're using and if it's AMD refuse to boot", but instead a simple "Well, we won't add the microcode that AMD's CPUs would need".


hhmmm....but since Android is open source, cant someone add the support for AMD.

---

### Post by Lucradia on 2011-01-16
> **sudoer541 said:**
> hhmmm....but since Android is open source, cant someone add the support for AMD.

Your processor says "Athlon 64"

Android is not meant to run on amd64 or x86-64, yet. There's no need to add support for it yet either.

If Athlon 64 isn't 64-bit, tell AMD that it was foolish to call such a processor as such.

---

