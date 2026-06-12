---
title: "Some things botheriing me about kubuntu 10.04"
date: 2010-04-02
forum: The Cafe
---

### Post by sandyd on 2010-04-02
1. It boots too fast! I cant even see my lovely plymouth bootscreen :(
2. The touchpad tap works out of the box (cant fiddle with SHMconfig anymore)
3. Really Really Really Fast. (Too fast for me, I like to wait a couple of seconds for it to start, and a couple of seconds for windows to fully maximize)
4. Has sound out of the box! (takes the fun out of fiddling with pulseaudio and whatnot)
5. Crashes really little, less than kde backports (no more bug reporting :( )
6. acetoneiso got added to the repos (will likely make me not go through the effort of adding getdeb)
7. ACPI works (Terminals not flooded with the EC: Input Buffer errors anymore. I liked them, they made it a challenge to type stuff in...)

---

### Post by inobe on 2010-04-02
that just flat out sucks carlee.

---

### Post by HoboJ on 2010-04-02
I too am bothered over kubuntu 10.04. I installed it on a year old toshiba laptop today and everything worked perfectly out of the box. Even the printer that I setup with it went off without a hitch. kubuntu 9.10 was far superior, I had to jump through many hoops just to set that up on this laptop. This is a real bummer.

---

### Post by inobe on 2010-04-04
the desktop activity settings really tips me off, it seems to work flawlessly, i don't have to rename .kde folder to reset my desk anymore, dammit :-x

---

### Post by Psumi on 2010-04-04
What I'm really bothered by is how good my OpenBox DE-less, DM-less minimal install of Debian/Ubuntu works all out of the box.

(On Debian, my wireless card is not configured due to the driver not being open source (ipw2000 or whatever.))

---

### Post by goldshirt9 on 2010-04-04
wow that is a shame.

---

### Post by phibxr on 2010-04-04
> **carlee said:**
> 1. It boots too fast! I cant even see my lovely plymouth bootscreen :(
2. The touchpad tap works out of the box (cant fiddle with SHMconfig anymore)
3. Really Really Really Fast. (Too fast for me, I like to wait a couple of seconds for it to start, and a couple of seconds for windows to fully maximize)
4. Has sound out of the box! (takes the fun out of fiddling with pulseaudio and whatnot)
5. Crashes really little, less than kde backports (no more bug reporting :( )
6. acetoneiso got added to the repos (will likely make me not go through the effort of adding getdeb)
7. ACPI works (Terminals not flooded with the EC: Input Buffer errors anymore. I liked them, they made it a challenge to type stuff in...)

You've still got time to report these as showstopper bugs! :D

---

### Post by NightwishFan on 2010-04-04
I tried Kubuntu as well. Sarcasm aside, I do have one major issue. Every time someone messages me on Kopete my sound cuts out on Amarok. This happens on OpenSUSE as well. Though they finally fixed some paper cut issues I had such as the plasma theme configuration being located next to the background setting. It really does belong in Appearance, though now it is hidden away! :lolflag:

Still, despite being quite awesome it looks like it is still Gnome for me on this release. I miss the perfection of KDE3, but whats done is done. :(


Edit: Psumi, do I need to mention your epic minimalism in my sig?

---

### Post by uljanow on 2010-04-04
Here are some quick fixes:

1. It boots too fast! I cant even see my lovely plymouth bootscreen :(
echo "sleep 5m > /etc/rc.local"

3. Really Really Really Fast. (Too fast for me, I like to wait a couple of seconds for it to start, and a couple of seconds for windows to fully maximize)
add kernel parameter mem=256M

4. Has sound out of the box! (takes the fun out of fiddling with pulseaudio and whatnot)
cat /dev/urandom > /dev/dsp

5. Crashes really little, less than kde backports (no more bug reporting :( )
while (true); do
    kill $RANDOM
done

---

### Post by NightwishFan on 2010-04-04
Wow, epic suggestions, I actually do mem=256m all the time to test memory pressure.

---

### Post by Psumi on 2010-04-04
> **NightwishFan said:**
> Edit: Psumi, do I need to mention your epic minimalism in my sig?

lol, do as you wish; I don't mind.

I'm not as new as you may think though.

---

### Post by NightwishFan on 2010-04-04
I do not think you are new, I never patronize anyone. :D I was just joking because you mentioned this in the last thread I was viewing by random chance I went to this one.

---

### Post by MooPi on 2010-04-04
Carlee you may be skirting the code of conduct with all of that blatant sarcasm. You may want to watch your step young lady :p

---

### Post by teh603 on 2010-04-05
Most of you probably don't know that my first KDE experience was on a Xandros-based eeePC 701, back in the days when WinXP wouldn't fit on an SSD and Win7 was a bad pipe dream. It was a horribly shitty one.

I just installed Kubuntu 10.04, and it feels like something out of Star Trek or Babylon 5. Almost everything works (I had to provide connection info for my cell modem, instead of having a connection helper applet), the surrogate for Synaptic works surprisingly well... yeah. Its really neat.

---

### Post by NightwishFan on 2010-04-05
The notifications are a nightmare in 4.4.. I am really really done with KDE. I just cannot handle such an active interface I will be using something much more boring.

---

### Post by sandyd on 2010-04-05
> **NightwishFan said:**
> The notifications are a nightmare in 4.4.. I am really really done with KDE. I just cannot handle such an active interface I will be using something much more boring.

the avanta notifications are gone :( i want them back...

---

### Post by NightwishFan on 2010-04-05
I agree, they were great. I tried KDE for two days and I was overwhelmed by how busy the interface is.

[QUOTE="NightwishFan"]
KDE: So and so has sent you a message.
NWF: ok..
KDE: So and so has sent you 3 more!
NWF: Ok.
KDE: Kwallet needs access!
NWF: Sure, allow access 'always'.
KDE: Kwallet needs access for this too!
NWF: Ok! Allow access always...
KDE: These people have sent you messages!
NWF: I am working! I get it!
KDE: Install this software?
NWF: Never show this again...
KDE: Are you getting any work done?
NWF: No you keep bothering me with large animated popups! *Crys*
[/QUOTE]

---

### Post by Elfy on 2010-04-05
moved back to cafe

---

### Post by MichealH on 2010-04-05
> **forestpiskie said:**
> moved back to cafe

Its true home :rolleyes:

---

### Post by sandyd on 2010-04-18
> **NightwishFan said:**
> The notifications are a nightmare in 4.4.. I am really really done with KDE. I just cannot handle such an active interface I will be using something much more boring.
I found something that may end your nightmare ;) ;)
[http://digitizor.com/2010/03/24/how-to-enable-a-ayatana-type-notification-in-kde-sc-4-4-ubuntu/](http://digitizor.com/2010/03/24/how-to-enable-a-ayatana-type-notification-in-kde-sc-4-4-ubuntu/)
in the part where they talk about removing the OSD thingy to install,
instead
just download the deb, and open it using file-roller or ark

open data.tar.gz

extract the "usr" folder into "/" (dont worry, its safe!)

That will get you through the install section of the guide
then go on with the rest of the instructions

note that you might need to add /usr/bin/colibri to your startup apps.

---

### Post by NightwishFan on 2010-04-18
Thanks for the tips Carlee. I will keep the option open in any case. What I said was above was not really fair anyway. I would be better off just giving my feedback or helping code the replacement.

---

### Post by armageddon08 on 2010-04-19
Is the Software Center available in Kubuntu Lucid?

---

### Post by NightwishFan on 2010-04-19
You can install it in KDE I am sure, but it is not ported to QT (I think). Considering Ubiquity is, they will probably port it to pyqt eventually.

---

### Post by TheNessus on 2010-04-19
> **NightwishFan said:**
> I tried Kubuntu as well. Sarcasm aside, I do have one major issue. Every time someone messages me on Kopete my sound cuts out on Amarok. This happens on OpenSUSE as well. Though they finally fixed some paper cut issues I had such as the plasma theme configuration being located next to the background setting. It really does belong in Appearance, though now it is hidden away! :lolflag:

Still, despite being quite awesome it looks like it is still Gnome for me on this release. I miss the perfection of KDE3, but whats done is done. :(


Edit: Psumi, do I need to mention your epic minimalism in my sig?


it's an amarok bug - either don't use sound notifications in Kopete or don't use Amarok.

---

### Post by NightwishFan on 2010-04-19
Thanks for the info! Yes, I disabled sounds in Kopete. I may switch to Juk on KDE though, Amarok is... meh. It sure scans my library fast though.

---

### Post by jkxx on 2010-04-19
Not really contributing anything to the Kopete bit except to say you're in the same boat with Trillian or Pidgin on Windows. So you won't be any better off using those :D

Really, it'd be nice if someone could make a messenger that has working sound notifications. Till then I'll at least have a good excuse for not responding to people in a timely manner..

---

### Post by A_T on 2010-04-19
Kpackagekit is still a horrible mess.

---

