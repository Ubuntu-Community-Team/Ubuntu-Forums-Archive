---
title: "foreign characters in the bash shell"
date: 2007-12-27
forum: Server Platforms
---

### Post by mellowd on 2007-12-27
Anyone know how to add foreign character support for the bash shell? I'm trying to properly display Hungarian characters when ssh'd in and this is what I see for example:

```
root@simba:/new_downloads/music# ls -lha
drwxr-xr-x 14 root root 4.0K 2007-12-25 18:22 .
drwxrwxrwx 26 root root 4.0K 2007-12-27 08:47 ..
drwxr-xr-x  2 root root 4.0K 2007-12-24 15:22 SebestyÃ©n MÃ¡rta - Szerelmeslemez
drwxr-xr-x  3 root root 4.0K 2007-12-24 15:25 VA - DBLaci KarÃ¡csony (Normalized) (2007)
```


anyone know how to fix this?

---

### Post by daou on 2007-12-27
If you are using gnome-terminal, you can do that in the menu:

Terminal->Set character encoding->Language code

You need to know which language code the file names are encoded with, however. Probably one that covers Hungarian.

---

### Post by mellowd on 2007-12-27
I have no gui installed at all on my server. They don't display correctly when I'm on the box or ssh'd in. there must be a way to configure the bash terminal but as yet I'm not sure how to.

---

### Post by daou on 2007-12-27
> **mellowd said:**
> I have no gui installed at all on my server. They don't display correctly when I'm on the box or ssh'd in. there must be a way to configure the bash terminal but as yet I'm not sure how to.

You don't need a GUI to change the options. If you are ssh'd in from a GUI, then you can change the gnome-terminal options from the client side, and it should work correctly. However, if even the client doesn't have a GUI, it's probably some bash environment variable that needs to be edited. Perhaps $LANG.

Format of LANG: language_COUNTRY.encoding

so for me 'echo $LANG' gives fi_FI.UTF-8

you probably want to change the encoding, so do
```
export LANG=lang_COUNTRY.encoding_with_hungarian
```

Replace lang and COUNTRY with your two letter ISO identifiers (keep the old ones... get them with the echo command)

---

### Post by daou on 2007-12-27
Country and language ISO codes: [http://www.w3.org/WAI/ER/IG/ert/iso639.htm](http://www.w3.org/WAI/ER/IG/ert/iso639.htm) (obsolete, there might be a more up to date resource on the net)

Looks like Hungarian is [B]ISO 8859-16 (character encoding)
[/B]

---

### Post by mellowd on 2007-12-27
Thanks, giving it a try now

---

### Post by mellowd on 2007-12-27
Hmm, still doesn't work.

This is what I've done so far:

I've added the hungarian locale like so:
```
root@simba:/usr/share/locales# ./install-language-pack hu
Generating locales...
  hu_HU.UTF-8... done
Generation complete.
root@simba:/usr/share/locales# dpkg-reconfigure locales
Generating locales...
  en_GB.UTF-8... done
  en_US.UTF-8... done
  hu_HU.UTF-8... up-to-date
Generation complete.
root@simba:/new_downloads/music# locale -a
C
en_GB.utf8
en_US.utf8
hu_HU.utf8
POSIX

```

I've then configured putty to display both central and easter european characters, but I'm still getting this:

```
root@simba:/new_downloads/music# ls -lha
total 56K
drwxr-xr-x 14 root root 4.0K 2007-12-25 18:22 .
drwxrwxrwx 26 root root 4.0K 2007-12-27 08:47 ..
drwxr-xr-x  2 root root 4.0K 2007-12-24 15:22 Sebesty&#258;©n M&#258;&#711;rta - Szerelmeslemez
drwxr-xr-x  3 root root 4.0K 2007-12-24 15:25 VA - DBLaci Kar&#258;&#711;csony (Normalized) (2007)
```

Anyone else have any ideas?

---

### Post by mellowd on 2007-12-27
Odd, in putty I changed the character set translation to Latin 2, which covers the Hungarian characters. Therefore putty is configured to show Hungarian characters and the server itself has the Hungarian locale. It still doesn't work, though now the offending letters have simply changed shape, but still wrong:

```
root@simba:/new_downloads/music# ls -lha
total 56K
drwxr-xr-x 14 root root 4.0K 2007-12-25 18:22 .
drwxrwxrwx 26 root root 4.0K 2007-12-27 08:47 ..
drwxr-xr-x  2 root root 4.0K 2007-12-24 15:22 Sebesty&#258;Šn M&#258;&#260;rta - Szerelmeslemez
drwxr-xr-x  3 root root 4.0K 2007-12-24 15:25 VA - DBLaci Kar&#258;&#260;csony (Normalized) (2007)
```

---

### Post by popch on 2007-12-27
Suggestion:

Can you type & echo your Hungarian characters, and can you display a text file properly which contains those?

It is perfectly possible that the problem does not lie (anymore) with the keyboard and display mapping but with the encoding used when writing those files. I.e., the encoding in the directory entries might be at fault. 

OTOH, is there an option which determines the character set of the file system? I now that that can become an issue with file servers such as Samba.

---

### Post by mellowd on 2007-12-27
I've tried creating a new file and pasting some Hungarian text. This is the original text:

```
Az eucharisztia (avagy úrvacsora) keresztény szertartás, mely Jézusnak a kenyérrel 
és borral kapcsolatos utolsó vacsorai szavait és cselekedeteit ismétli meg liturgikus módon. 
Az eucharisztiát/úrvacsorát minden keresztény felekezet (a maga teológiai el&#337;feltevéseinek megfelel&#337;en) 
szentségnek tekinti.

Az eucharisztia szó több jelentéssel bír: egyrészt a kenyérrel és a borral végzett 
liturgikus cselekményt jelöl, ebb&#337;l pedig &#8211; pars pro toto alapon &#8211; a katolikus és ortodox 
szóhasználatban az egész szentmisét, illetve liturgiát). Ebben az értelemben használva 
kis kezd&#337;bet&#369;vel írjuk. A hazai (és nemzetközi) protestantizmus (ideértve mind a 
református és evangélikus egyházat, mind az egyéb protestáns és neoprotestáns 
felekezeteket) terminológiájában az eucharisztikus szertartásra a szokásos kifejezés 
az úrvacsora. Másrészt az Eucharisztia &#8211; katolikus és ortodox hitvallás szerint &#8211; 
jelenti a kenyér és a bor színe alatt valóságosan jelen lév&#337; Jézus Krisztust is. 
Ebben az értelemben &#8211; mivel személyre utal &#8211; bevett szokás a nagy kezd&#337;bet&#369; használata, 
s ilyen értelemben szinonimája az Oltáriszentség.
```

When I paste it into my new files this is what I see:

```
Az eucharisztia (avagy &#258;&#351;sora) kereszt&#258;&#352; szertart&#258;&#260; mely J
&#258;&#352;snak a keny&#258;&#352;el &#258;&#352;borral kapcsolatos utols&#258;&#322;csorai szavait &#258;&#352;cselekedeteit 
ism&#258;&#352;i meg liturgikus mhariszti&#258;&#258;&#351;sor&#258;&#260;minden kereszt&#258;&#352; felekezet 
(a maga teol&#258;&#322;i el&#258;&#318;tev&#258;&#352;inek megfelel&#258;&#318; szents&#258;&#352;ek tekinti.

Az eucharisztia sz&#258;&#322;bb jelent&#258;&#352;el b&#258;* egyr&#258;&#352;t a keny&#258;&#352;el &#258;&#352;a borral 
v&#258;&#352;ett liturgikus cselekm&#258;&#352;t jel&#258;&#347;ebb&#258;&#318;edig . pars pro toto alapon . 
a katolikus &#258;&#352;ortodox az eg&#258;&#352; szentmis&#258;&#352; illetve liturgi&#258;&#260;. Ebben 
az &#258;&#352;elemben haszn&#258;&#260;a kis kezd&#258;&#318;&#258;&#357;&#258;*uk. A hazai 
(&#258;&#352;nemzetk&#258;&#347; protestantizmus (ide&#258;&#352;ve mind a reform&#258;&#260;s &#258;&#352;evang&#258;&#352;kd 
az egy&#258;&#352;protest&#258;&#260; &#258;&#352;neoprotest&#258;&#260; felekezeteket) termin&#258;&#260;n az 
eucharisztikus szertart&#258;&#260;a a szok&#258;&#260;s kifejez&#258;&#352;az &#258;&#351;sora. M&#258;&#260;&#258;&#352;t az Eucharisztia . 
katolikus &#258;&#352;oitvall&#258;&#260;szerint . jelenti a keny&#258;&#352;&#258;&#352;a bor sz&#258;* alatt val&#258;&#322;osan jelen l&#258;&#352; 
J&#258;&#352;s Krisztust is. Ebben az &#258;&#352;elemben . mivel szem&#258;&#352;re utal . bevett szok&#258;&#260;a nagy 
kezs ilyen &#258;&#352;elemben szinonim&#258;&#260; az Olt&#258;&#260;szents&#258;&#352;
```

So now even with a brand new file it doesn't display :(

I can't even seem to echo any character (for example, è [ALT+138]) displays nothing.

---

### Post by koenn on 2007-12-27
half-educated guess :
it could have something to do with the font your console uses. 
Since you're ssh'ing to the server (or sitting at its console), I assume the font you get is the console font of the server. 

Now, if a key code you send, eg ALT+138, doesn't have a glyph in that character set, you get a blank. Otherwise you get whatever character that is mapped to that key code in the font you're using. 

On the server, have a look in /usr/share/fonts. 
Then try to change the font with setfont or one of the related tools mentioned at the end of 'man setfont' [http://linux.die.net/man/8/setfont](http://linux.die.net/man/8/setfont)

background : [http://linuxgazette.net/issue91/loozzr.html](http://linuxgazette.net/issue91/loozzr.html)


Although I would expect this to be handled by "locale".
you might want to have a look at the LC_ variables and try to set those
[http://linux.die.net/man/1/locale](http://linux.die.net/man/1/locale)

---

### Post by mellowd on 2007-12-27
> **koenn said:**
> half-educated guess :
it could have something to do with the font your console uses. 
Since you're ssh'ing to the server (or sitting at its console), I assume the font you get is the console font of the server. 

I'm not entirely sure, and this is why. When I ssh in through putty, I get a different font to when I ssh in via absolute terminal. the same problem lies with both fonts though. I'm going to read through the links you sent me. Also, when I get home from work later I'm going to plug a monitor into my server to see exactly what characters I get on the screen. At least that will show where my problem lies. If I'm getting the right characters then my client is somehow still screwed up (even though its on Latin2) if it's wrong I know it's definately something on the server.  Thanks for all the suggestions so far

---

### Post by koenn on 2007-12-27
> **mellowd said:**
> I'm not entirely sure, 
hm, yes, come to think of it, when you're remote, you may well just receive a code for a character to put onscreen, and then it's your client, be it an x-terminal, putty, or a tty,  that has to pick up the corresponding glyph, so it may be very well a client-side config issue.

---

