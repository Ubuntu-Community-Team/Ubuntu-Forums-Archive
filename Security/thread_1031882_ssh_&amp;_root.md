---
title: "ssh &amp; root"
date: 2009-01-05
forum: Security
---

### Post by biovore on 2009-01-05
First off let me say that SSH + root is a bad Idea in any condition.  But for those of us that are stuck with having to have it, what should we do?  

I got a close source POS, that dosen't understand the greatness of sudo.  It is targeted at redhat/suse people who (by default) have ssh root access.  What I would like to do is; allow root logins via SSH from designated IP's only.  I am not 100% sure how to go about this. And would like some assistance and feed back on solutions and ideas?

---

### Post by Dr Small on 2009-01-05
> **biovore said:**
> First off let me say that SSH + root is a bad Idea in any condition.  But for those of us that are stuck with having to have it, what should we do?  

I got a close source POS, that dosen't understand the greatness of sudo.  It is targeted at redhat/suse people who (by default) have ssh root access.  What I would like to do is; allow root logins via SSH from designated IP's only.  I am not 100% sure how to go about this. And would like some assistance and feed back on solutions and ideas?
Why not setup key based authentication and disable password authentication, so scriptkiddies can't bruteforce the root account?

---

### Post by bodhi.zazen on 2009-01-05
I second the idea of using keys.

Other options include:

1. Take a look at hosts.allow and hosts.deny

2. You can use your firewall (iptables). If you do not know how to use iptables, use a configuration tool such as ufw  (or gufw).

3. Install something such as denyhosts or fail2ban (to limit attempts to log in).

---

### Post by scorp123 on 2009-01-06
> **biovore said:**
>  I got a close source POS, that dosen't understand the greatness of sudo.  Welcome to the club :twisted:  I had to enable the "root" account on my Ubuntu and I have to run Ubuntu's 32-bit server kernel with PAE enabled because the closed source stuff I have to use doesn't work with 64-bit Linux .... ](*,)

> **biovore said:**
>  It is targeted at redhat/suse people who (by default) have ssh root access.  What I would like to do is; allow root logins via SSH from designated IP's only.  What's the application you're trying to use?

What I did: I use **denyhosts** and I reconfigured it to be very merciless. Two false login attempts and the host where the connection originated from gets completely blocked - forever in this case (or until I remove the entry again). I highly recommend it. So if someone starts attacking your machine and keeps trying to login via "root" he only has 2 attempts to get the password right. There is no third chance. Of course: the password should be something complicated. I use **pwgen** for this and let it generate passwords for me. This makes guessing very very hard.

Denyhosts tutorial:
[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

Different than described in the tutorial (which is a bit old now) you can easily install "denyhosts" via apt-get or Synaptic, you don't need to manually download the package any more.

One more from the Ubuntu forums, based on the one above:
[http://ubuntuforums.org/showthread.php?t=254149](http://ubuntuforums.org/showthread.php?t=254149)

Newer tutorial but a bit short IMHO:
[http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)

"pwgen" is straightforward ... just install it (sudo apt-get install pwgen) and then execute it ... it will instantly generate strong passwords. If you play with the parameters you can force it to create insanely hard passwords. Example:
```

> pwgen -c -n -y
Ue8Ji'm8 dae)f9Ee Thei$th8 Ji9aeGh] Foo?d0Oh ej`o0Ai4 bu:Toth5 xuB$o2si
ouV1sua] Lei6Fae^ ru7ea)Le Iesh{ee2 As%u1iZ@ Esei[ch4 MaeH"ah6 oPh8ga%H
Xiy5xei) aCh>ohz4 booF2op< gah$v2Wa Jae5aub! OoR6Ae\l viec4Ji+ so=Thae2
hie6Aeh) SaeC(ee9 nea<V1Be oa*Pee1P Je1cooh- Jah6Co|d od<e7OhT yee.ch7U
ahta'Th7 ooG'ai3i Rie2ete_ Eic7Eem$ ro2Na|v\ Kie2Iex$ EHee,y5h oe^d4AeN
Moo\Koo6 sho0Hoh( Fa1faZ.o aeG2su$b juNg8ee\ aiR1Yoh. Ao5ya@m0 ai9EMoo/
Isai#da4 Eech9ug_ ooBie<m3 aeTh:ae0 noo8Noo] eiR5hoo> uac2Xoo[ aev$eX8r
ax9nuY'u mohB=ur5 Ri\e2ume hai.V2ee Zix{ii3a Ah@ie3lu eep.aeG1 wai9Hee{
ahh~oeY1 Ee2Chee> Uo,t8ea> aiG7aph} Wai`h6ED Quoo[V7k ooP>ahk2 iuy@oh7V
Vona(pu9 chei*w8B Ra7au*pa ua6Gie$d Oa&H4fee johM1pe: uth}e6Ch Thai@qu1
aec[ooH7 Le6AC?u7 aCh{a8ei Ia<ghe1r aZ]ihi8e Xei%Wee1 She'y5Ei If3Ohj@e
po?Vae4i Qua%v0Sh da7ak$aW Aif4Loh. Ohc0nee" ahW0jig* Aep+ai2g poh]Sh9z
een8Zo}o Mu$m1ea6 Aivu_N0b Choe&g9o eig"oh1Y Ye4eigh^ teJ3Ohz; ue#f2Soz
Doh9aa<L phae'v9G Tohb*e4t ahR0die& moh8Vah! boh*B3ae Jaa0rai' Je1eeQu_
uu^s3Lai Hai-Gh7A aiS8dah. aeK9iez# ohWei#k3 Yee9ohm{ AV7feeh? Duo3qua.
Cee3jai. Hoh8ohr& su:zaTe2 aeZ$eet6 ePa&ish9 tei_S6ei EiK8hug, Equ/e4ch
Paeng#u3 mee<b3Sh Avo;ng1f we5Oigh/ Oht1bee> eiJai&d0 ECh1aeP} Exii)Y0D
ha|Mee0u Yai2Lov( zieP+oo6 iB4Aiyu] nah|Zae7 Aa'goTe9 Ik+ae@g1 iP'i)ki3
Ei_g1wai eiP.u6xu ue7Gegi& IeM6koh* Rie`zi0O aeTh,a7i zoh!Qu1m ga!i)Ph1
ooPe"d1a uo1EeGh" de1AiH(u noN7moo" Ue#W1je8 bae"W9Ai ui:Faer8 jei3Uu`f

```

I am pretty sure that a hacker will have one hell of a hard time guessing a password such as any from above with only two attempts given to them by "denyhosts" .... :D

---

