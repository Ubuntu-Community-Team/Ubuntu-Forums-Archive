---
title: "Tethered to 3G? You need to know how to reduce your data use"
date: 2012-01-02
forum: The Cafe
---

### Post by jjpcexpert on 2012-01-02
I'm currently tethered to a 4G connection so this page will be graphics-light as I have graphics display disabled in my browser Iceweasel (like Firefox). So let us get moving with this guide.

First things are first. So open up your browser.
In your browsers settings, find out where to disabled automatic loading of images and pictures. In Firefox, it's Edit/Tools > Preferences > Content > Load images automatically. Uncheck this, and also uncheck "Enable Java", as that when enabled hogs bandwidth.
Now find out where your plugins section is in your browser. Again, using Iceweasel as the example, it's in
Tools > Add-ons > Plugins. Disable every plugin there is, as Flash and video playback hog bandwidth and your data allowance. I've got a data cap on my dad's Rogers (6GB between Dad and Mum, but I cap myself at 0.17GB to avoid haemorrhaging their bank account ;)) And that is NOT it.

Now you need IPTables.

Set a rule on chain OUTPUT to quota 160 MB and drop the rest.
```
$ sudo iptables -A OUTPUT -p tcp -m quota --quota 167772160 -j ACCEPT ; sudo iptables -A OUTPUT -p tcp -j DROP
```Check you have at least 200 MB left on your cellular phone account though! You'll need 40MB in emergencies. Or change the 167772160 for however many bytes you can afford.
If you are a child using your mum's or papa's Internet access on mobile cellular, please seek permission from the billpayer(s) before using their access. I'm allowed up to 5 MB in one fix, which is a lot of websites - but not a lot of data. 160MB is less than what is left, so I should be allowed about that much. Also, in GNOME if you have it, open the System Monitor. In Debian it is in Start Bar/Menu > Applications > System Tools, in Ubuntu it is in Start Bar/Menu > System > Administration. I've already used 4 MB of my 5 MB, so bye-a and hope you enjoy using this guide!

---

### Post by LowSky on 2012-01-02
I'm so glad I don't have a cap.

---

### Post by Drenriza on 2012-01-02
> I'm currently tethered to a 4G connection
My first question is, is this a real 4G connection or is it a 3G-LTE?

This this guide for a mobile or a stationary device? If it's for a mobile device, which?
Or is it for any Ubuntu device using a xG network?

---

### Post by 3rdalbum on 2012-01-02
Or you could use Opera as your web browser with Opera Turbo turned on. It employs a compression proxy like in Opera Mini to reduce data use.

---

### Post by jjpcexpert on 2012-01-02
It's HSPA. It's AFAIK it's a pre-4G HSPA+ connection because I am in a rural area served by a very near urban transmitter.

---

### Post by jjpcexpert on 2012-01-02
What about open source mavericks? They never use Opera. I did the FOSS maverick's version, despite not being one.

---

### Post by jjpcexpert on 2012-01-02
And you flaming well should be Lowsky. Because Rogers are very limiting - their biggest Internet package on mobiles is 10GB.

---

### Post by 3rdalbum on 2012-01-03
> **jjpcexpert said:**
> And you flaming well should be Lowsky. Because Rogers are very limiting - their biggest Internet package on mobiles is 10GB.

Amaysim's is 4 GiB and I'm with them. I've never even used 500 MiB in a month, except when I was purposely using up as much data as I could before the month rolled over, by torrenting and downloading Ubuntu updates! I do heavy surfing of Cheezburger sites such as Memebase, Very Demotivational, Comixed, etc which are basically all images.

However, I'm not sure if Amaysim's data use tracking is unaccurate in my favour, or if they're just honest and every other carrier is not. (probably a bit of both).

---

### Post by szymon_g on 2012-01-03
it would be helpful if ubuntu would support delta-packages /same as fedora or opensuse/. once, it saved me 96% of data /i.e during update i had to download 4 mb instead of 100mb/- but averagely it saves ca. 80-85%

---

### Post by tlcstat on 2012-01-03
Greetings,
I don't need to reduce my data use since I have unlimited data. I still try to keep it a 5G month. Only problem that I have is if I'm doing a big download like updating my TomTom map I occasionally have to cool my phone with a freezer gel pack. Else it goes into overheat. 100% mobile broadband and loving it! Works great on bluetooth also. 
tlcstat

---

### Post by t0p on 2012-01-03
I know what a pain it can be if you're using a 3G device (eg cellphone) to connect a computer to the internet when you have a data cap or pay-per-use plan.  One way to reduce data throughput is to use the web browser Opera Mini, as with this browser an Opera server fetches the web page you've requested then optimises it for cellphone use - compressing the page quite a lot.  Thing is, Opera Mini works on cellphones, not computers, so you have to use a cellphone emulator.  Look [here]("http://shiliarr95z.weebly.com/2/post/2011/08/how-to-access-banned-site-using-ubuntu-and-android.html") for Ubuntu-friendly info.

---

### Post by jjpcexpert on 2012-01-03
Well to avoid blowing up your phone you could use a cool gel pack, but that's another topic. I'm tethered to capped data, because capped is all that is available in Maple Ridge - even on landline broadband Internet! So mobile broadband - double yes. Keep within cap - triple yes! If you don't get a cap, then keeping your phone cool is also double yes.

---

### Post by jjpcexpert on 2012-01-03
Got to give that suggestion to Debian. They handle all installation of software - by making the program we use to download from the repositories. And heck, that program is in the repositories as "apt".

---

