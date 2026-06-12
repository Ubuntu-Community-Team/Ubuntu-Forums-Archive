---
title: "GShutDown - We need translators !"
date: 2006-12-29
forum: The Cafe
---

### Post by Maxime81 on 2006-12-29
Hi,

GShutDown ( [http://gshutdown.tuxfamily.org/en/](http://gshutdown.tuxfamily.org/en/) ) is an advanced shutdown utility which allows you to schedule the shutdown or the restart of your computer. With it you can simply and quickly choose the turn off time.
GShutDown communicates directly with GDM or KDM and your window manager to shutdown cleanly your computer and without be root.
A first release is available since September but the software is still available in only 2 languages !
So if you speak any other language than English and French (we are french speakers) and have the time to translate this little soft, please contact us : gshutdown AT gmail DOT com.

Thanks.

p.s. there are maybe some english mistakes so thanks to signal us any errors you'll find.

---

### Post by Hex_Mandos on 2006-12-29
I proposed myself to translate into Spanish. It's great to have a way to collaborate with Free Software for those of us who can't code.

---

### Post by Maxime81 on 2006-12-30
Yes, thank you.

Currently we have : sweeden and spanish
Is there anyone for german, italian and chinese (and of course any other languages) ?

To translate it's easy :

You need : svn, poedit (and perhaps other softwares)
Download the gshutdown source code (for the svn : svn co svn://svn.tuxfamily.org/svnroot/gshutdown/gshutdown )
Go to gshutdown/po
run : ./update_po
and launch poedit : poedit
When the first configuration is done, : file > new catalog from pot file (or a sentance like this... I don't have poedit in english ;) )
Translate :) And send us the xx.po file.

---

### Post by PartisanEntity on 2006-12-30
How much text is there to translate? Depending on the amount of text I might be able to help with German.

---

### Post by Maxime81 on 2006-12-30
It's very short : near 100 strings (with an average of 5 words by string)


You can start a translation and someone else will do the end, that's not a problem.

---

### Post by Gargamella on 2006-12-30
How do we translate it? Is it simple (just like launchpad)?

If I don't need coding knowledge, I will translate it in Italian

---

### Post by Maxime81 on 2006-12-30
As explained, we use the software poedit.
It's very easy. (I've just found an example : [http://www.jalug.org/Members/pigeonflight/blog/poedit-translations/](http://www.jalug.org/Members/pigeonflight/blog/poedit-translations/) )

You don't need any coding knowledge.

---

### Post by macogw on 2006-12-30
I can attempt Japanese.  A lot of the symbols (at least for the dates) will be the same as for Chinese.

---

### Post by Kayne on 2006-12-30
I could do the German translation.

---

### Post by dbbolton on 2006-12-30
do you need french ?

---

### Post by macogw on 2006-12-30
> **dbbolton said:**
> do you need french ?
The app-writers are French, so no (says in the first post).

---

### Post by haxer on 2006-12-30
I have almost completed the translation to swedish im just going to check it and see if there are any things i forgot :)

---

### Post by kripkenstein on 2006-12-30
As already mentioned in this thread, why not allow translations to be done on Launchpad? Lots of projects do, it's extremely convenient :)

---

### Post by macogw on 2006-12-30
poedit seems pretty easy to use, to me.  i havent seen the launchpad method either though

---

### Post by haxer on 2006-12-30
I dont know but i think its kind of od that you translate it and then i says "here i am" and you translate it to "here i am" in some other language then it says on the paper you save first "here i am" then in your language "here i am" they program shoves both after saving.

---

### Post by Maxime81 on 2006-12-30
Thanks dbbolton but, indeed, we both speak french :).
Achraf is from Morocco and I'm french.

---

Merci dbbolton mais, en effet, nous parlons tous les deux français :).
Achraf est du Maroc et je suis français.

---

Thanks to all translators who are currently working on the translation.
Indeed we could used launchpad but here, gshutdown is a little software and the translation is easyer when you understand precisly what we wanted to say.
And for the contributors there is an advantage ! Your name in the about window :P.

I really understand the need of launchpad for big projects but here... But maybe later, for some languages in particular...

oh and now, after reading me, you understand better why I said you're pleased to notice us all the english errors :). Nop ?

---

### Post by RainCT on 2007-01-01
I'm working on the catalan translation ;)

---

### Post by sn0m on 2007-01-01
I could have a go at translating it to Albanian, let u know how i am getting on.

---

### Post by Maxime81 on 2007-01-01
Thank you all.

Don't forget using the last version from the SVN :).

svn co svn://svn.tuxfamily.org/svnroot/gshutdown/gshutdown

The .pot file is in the po directory.

If you prefer : [http://svnweb.tuxfamily.org/filedetails.php?repname=gshutdown%20(gshutdown)&path=%2Fpo%2Fgshutdown.pot&rev=0&sc=0](http://svnweb.tuxfamily.org/filedetails.php?repname=gshutdown%20(gshutdown)&path=%2Fpo%2Fgshutdown.pot&rev=0&sc=0)

---

### Post by Hex_Mandos on 2007-01-01
I've had little time, but I'm more than halfway through with Spanish. :)

Update: Finished!

---

### Post by Maxime81 on 2007-01-01
RainCT and Hex_Mandos :
How time is needed to translate gshutdown ?

Note : the SVN version of gshutdown is now translated in :
English, French, Catalan, Spanish, Portuguese and Swedish.

---

### Post by Hex_Mandos on 2007-01-01
I suppose it depends on how comfortable one is with using tools like svn and poedit. I'd never used them before, so I took longer learning to use the tools than actually translating. Still, with all the inconveniences, I'd say it's less than two hours of work (as a VERY conservative estimate). I did it split in two parts, of roughly 50 messages each. I don't know how long I took for the first half, but today I only spent around 15 minutes finishing it.

---

### Post by Maxime81 on 2007-01-03
Is there anyone who is working on the german or the italian translation ?

---

### Post by utabintarbo on 2007-01-03
I speak Jive.

;) :p

---

### Post by Maxime81 on 2007-01-09
Nobody speaks german ? => ok.

---

### Post by Maxime81 on 2007-01-17
Currently we have :

      Catalan
      English
      French
      German
      Portuguese
      Russian
      Spanish
      Swedish

Is there anyone who is working on another translation ?

---

### Post by dorcssa on 2007-01-17
```
xxxxx@xxxx:~$ sudo aptitude install svn
Csomaglisták olvasása... Kész
Függ&#337;ségi fa építése... Kész
A kiterjesztett állapotinformáció beolvasása
Csomagállapotok inicializálása... Kész
Tag adatbázis építése... Kész
Nem találtam "svn" nev&#369; csomagot, de az alábbi
csomagok neve tartalmazza ezt: "svn":
  kdesvn websvn libapache2-svn libsvn-ruby libsvn-notify-perl rapidsvn
  libsvn-javahl svn-arch-mirror python2.4-svn svncviewer libsvn-simple-perl
  git-svn libsvn0 kdesvn-kio-plugins libsvn-mirror-perl libsvn-ruby1.8
  python-svn svn-workbench libsvn-core-perl libsvn-dev svn-buildpackage
  libsvn-doc latex-svninfo esvn svnmailer libsvn0-dev
  nautilus-script-collection-svn esvn-doc libsvncpp-dev cvs2svn
  libsvncpp0c2a python2.3-svn

```So..whcich to install? I'm up to translate it to hungarian, by the way. I'm just too new to linux, and need to learn the methods. :)

---

### Post by haxer on 2007-01-17
omg :P read all of this in this post !! go back to 1st page and just read :)

---

### Post by drfalkor on 2007-01-17
I'll do norwegian translation :)

---

### Post by dorcssa on 2007-01-17
> **haxer said:**
> omg :P read all of this in this post !! go back to 1st page and just read :)

Ok, I did a search in synaptic, and found a name subversion(aka.svn) So this is it? The post about how to do it just tells svn...

edit: Ok, obviously, this was it. Sorry for being a noob, starting the translation. :) Just to make it clear..I have to send it to the official e-mail adress, right?

---

### Post by Maxime81 on 2007-01-17
To resume :

You must have svn (sudo apt-get install subversion)

Download the last version :
svn co svn://svn.tuxfamily.org/svnroot/gshutdown/gshutdown

Go in the po directory :
cd gshutdown/po

Here you have the translations.
If you want to improve a translation you can do :
poedit XX.po (XX is the language, fr for french, es for spanish...)

If you want to do a new translation, open poedit :
poedit
So you can make a new catalog from the gshutdown.pot file :
File > New catalog from pot file (or something like this)
Select the gshutdown.pot file which is in the po directory.

When is done (and saved), send us your .po file at gshutdown aaaatttttt gmail.com

We'll add it in the SVN as soon as possible and also put your name in the about box ^. ;)


Thanks for you contribution !

---

### Post by dorcssa on 2007-01-17
Ok, e-mail went. This is my first translation, ever(according to program files, because of computing language, writings from newspaper doesn't matter I think), so I'm just hoping everything will be okay. Maybe I don't now the accurate phrase for some thing in my language, and I made up own..that was the best I could do. :)

---

### Post by hesee on 2007-01-17
Anyone working on finnish yet? I started my attempt. This is my first actual translation, but not so big, so probably i can do good enough package.


Hey, what about these kind of strings: T_est, how do you translate these (e.g. for german, swedish)?

---

### Post by BuffaloX on 2007-01-17
This looks cool :)

I did danish translation.

Can it make the power button work too?
In gnome it only raises the shutdown menu.
EXTREMELY annoying,
because I have to turn on the monitor to turn off the system.

---

### Post by dorcssa on 2007-01-17
> **hesee said:**
> Anyone working on finnish yet? I started my attempt. This is my first actual translation, but not so big, so probably i can do good enough package.


Hey, what about these kind of strings: T_est, how do you translate these (e.g. for german, swedish)?
It's not the same? Or close..? It was easy for me, T_eszt..only plus one letter. :mrgreen:

---

### Post by Maxime81 on 2007-01-17
Thanks a lot guys !

Think to have the last version of the gshutdown.pot file to work.
And I've forgotten :

gtk-* is not to translate !
"shutdown" "reboot" "logout" it the sentance : "Available actions are : \"shutdown\", \"reboot\" or \"logout\"" Must stay in english (for the moment. And it's for the command line => it's in english for less bugs due to "ôéàç..." letters or due to the translation)
It's the same for : 
"You cannot call --launch-after-delay, --launch-at or --launch-now at the same time.\n"

and 

"The authorized values in --action option are : shutdown, reboot or logout\n"



We'll make an RC1 release in 2 weeks. But just before it would be great if you can check your translation (there are severals changes). So I'll be in touch.

---

### Post by hesee on 2007-01-17
> **dorcssa said:**
> It's not the same? Or close..? It was easy for me, T_eszt..only plus one letter. :mrgreen:

Maybe this is more clear to you. Comes from "Time" and "Estimate" probably...  Oh, in finnish it looks stupid, maybe better leave as it is...

Edit: ah, now that I tested the actulal program it's more clear: it must be Test with e underlined, ok all clear,

---

### Post by dorcssa on 2007-01-17
> **Maxime81 said:**
> Thanks a lot guys !

Think to have the last version of the gshutdown.pot file to work.
And I've forgotten :

gtk-* is not to translate !
"shutdown" "reboot" "logout" it the sentance : "Available actions are : \"shutdown\", \"reboot\" or \"logout\"" Must stay in english (for the moment. And it's for the command line => it's in english for less bugs due to "ôéàç..." letters or due to the translation)
It's the same for : 
"You cannot call --launch-after-delay, --launch-at or --launch-now at the same time.\n"

and 

"The authorized values in --action option are : shutdown, reboot or logout\n"


We'll make an RC1 release in 2 weeks. But just before it would be great if you can check your translation (there are severals changes). So I'll be in touch.

Sorry, I wasn't aware..as I mentioned, I'm not experianced. :oops: I hope it's not a big problem to reverse those sentences. :)

edit: I ran trough the new one(not so much change). You missed to reverse one gtk-* but everything else look fine I think..by the way I put in the names of the new translators. ;)

---

### Post by Gargamella on 2007-01-18
I am translating in italian

---

### Post by Gargamella on 2007-01-18
I've finished the translation!

now sending

---

### Post by Redache on 2007-01-18
I can do it for Welsh, Not that Welsh will end up being a popular language choice, it's still cool to have :P.

---

### Post by Maxime81 on 2007-01-18
Lol why not :P.

In fact we accept : ;)

aa	Afar
ab	Abkhazian
ae	Avestan
af	Afrikaans
ak	Akan
am	Amharic
an	Aragonese
ar	Arabic
as	Assamese
av	Avaric
ay	Aymara
az	Azerbaijani
ba	Bashkir
be	Belarusian
bg	Bulgarian
bh	Bihari
bi	Bislama
bm	Bambara
bn	Bengali
bo	Tibetan
br	Breton
bs	Bosnian
ca	Catalan
ce	Chechen 
ch	Chamorro
co	Corsican
cr	Cree
cs	Czech
cv	Chuvash
cy	Welsh
da	Danish 
de	German
dv	Divehi
dz	Dzongkha
ee	Ewe
el	Greek
en	English
en_US	American English
en_GB	British English
en_AU	Australian English
eo	Esperanto
es	Spanish
et	Estonian
eu	Basque
fa	Persian
ff	Fulah
fi	Finnish
fj	Fijian
fo	Faroese
fr	French
fr_BE	Walloon
fy	Frisian
ga	Irish
gd	Gaelic
gl	Gallegan
gn	Guarani
gu	Gujarati
gv	Manx
ha	Hausa
he	Hebrew
hi	Hindi 
ho	Hiri Motu
hr	Croatian
ht	Haitian
hu	Hungarian
hy	Armenian
hz	Herero
ia	Interlingua
id	Indonesian
ie	Interlingue
ig	Igbo
ii	Sichuan Yi
ik	Inupiaq
io	Ido
is	Icelandic
it	Italian
iu	Inuktitut
ja	Japanese
jv	Javanese
ka	Georgian
kg	Kongo
ki	Kikuyu
kj	Kuanyama
kk	Kazakh
kl	Greenlandic
km	Khmer
kn	Kannada
ko	Korean
kr	Kanuri
ks	Kashmiri
ku	Kurdish
kw	Cornish
kv	Komi
ky	Kirghiz
la	Latin
lb	Luxembourgish
lg	Ganda
li	Limburgan
ln	Lingala
lo	Lao
lt	Lithuanian
lu	Luba-Katanga
lv	Latvian
mg	Malagasy
mh	Marshallese
mi	Maori
mk	Macedonian
ml	Malayalam
mn	Mongolian
mo	Moldavian
mr	Marathi
ms	Malay
mt	Maltese
my	Burmese
na	Nauru
nb	Norwegian Bokmaal
nd	Ndebele, North
ne	Nepali
ng	Ndonga
nl	Dutch
nl_BE	Flemish
nn	Norwegian Nynorsk
no	Norwegian
nr	Ndebele, South
nv	Navajo
ny	Chichewa
oc	Occitan
oj	Ojibwa
om	Oromo
or	Oriya
os	Ossetian
pa	Panjabi
pi	Pali
pl	Polish 
ps	Pushto
pt	Portuguese 
qu	Quechua
rm	Raeto-Romance
rn	Rundi
ro	Romanian
ru	Russian
rw	Kinyarwanda
sa	Sanskrit
sc	Sardinian
sd	Sindhi
se	Northern Sami
sg	Sango
si	Sinhalese
sk	Slovak
sl	Slovenian
sm	Samoan 
sn	Shona
so	Somali
sq	Albanian
sr	Serbian
ss	Swati
st	Sotho, Southern 
su	Sundanese 
sv	Swedish
sw	Swahili
ta	Tamil
te	Telugu
tg	Tajik
th	Thai
ti	Tigrinya
tk	Turkmen
tl	Tagalog
tn	Tswana
to	Tonga
tr	Turkish
ts	Tsonga
tt	Tatar 
tw	Twi
ty	Tahitian
ug	Uighur
uk	Ukrainian
ur	Urdu
uz	Uzbek
ve	Venda 
vi	Vietnamese
vo	Volapuk
wa	Walloon
wo	Wolof
xh	Xhosa
yi	Yiddish
yo	Yoruba
za	Zhuang
zh	Chinese
zu	Zulu

---

### Post by Kuoi on 2007-04-27
I've just send you ( Max ) the Dutch translation .

For your information ...

You can use it for both of these , because we Belgians speak Dutch .
nl Dutch
nl_BE Flemish

Greetings,  Kuoi

---

