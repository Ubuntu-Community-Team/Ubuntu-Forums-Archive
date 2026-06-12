---
title: "Hi guys how can you follow these small numbers ¹²³?"
date: 2013-02-27
forum: The Cafe
---

### Post by shantiq on 2013-02-27
a bit puzzled

tried to follow these numbers so i can get 0 ++> 9


but keyboard only yields  ¹²³     produced with Alt+Gr 123

how can i get 0456789 in the same way

tried fonts in Libre Office
and so far see none   tried google and no answer


i am sure one of you clever guys here know the answer



thanx in advance shan

---

### Post by vasa1 on 2013-02-27
I'm not sure what you're working with, but if it's html, you can make whatever you want appear as superscript using < sup > and < /sup > tags (without spaces).

Another thing I use is ReText from the repos for markdown:

---

### Post by Paqman on 2013-02-27
> **shantiq said:**
> 
tried fonts in Libre Office
and so far see none   tried google and no answer


Try Right click > Style > Superscript. You can also add it to a button on the toolbar if you're going to be using it a a lot.

---

### Post by schragge on 2013-02-27
It depends on what program you're entering these characters in. For libreoffice, **Paqman** already gave the answer. When entering superscripts using **AltGr** you're actually inserting special Unicode characters. There are Unicode characters for all superscript digits, but not all fonts support them beyond 3, e.g. *DejaVu Sans ExtraLight* only has glyphs for 01234. To see if they are supported by your console font, try
```

eval echo \$\'\\u207{4..9}\'

```

However, when using techniques described by **vasa1** and **Paqman**, normal digits get rendered as small superscripts, so these will work with any font, but only when rendered by specific software (HTML browser, LibreOffice).

---

### Post by dargaud on 2013-02-27
Another way is to get yourself a 'Compose key'. I use the useless Caps Lock key as a compose key: in KDE, [System Settings][Keyboard][Advanced][Compose key position] and select [Caps lock].
Then press that key to 'compose' two keys into the closest thing. For instance [`] and [e] will give [è]. In your case it's [0~9] and [^] which gives &#8304;¹²³&#8308;&#8309;&#8310;&#8311;&#8312;&#8313;...

---

### Post by shantiq on 2013-02-27
Thanx for prompt replies guys this is what i love most about our Ubuntu community... :KS


&#9679; the htlm trick is good but only for html    cannot be copied and pasted in text or anywhere   if so it reverts to normal numbers   so thanx for the tip with <sup>   will use when i need to write html pages   but i really want a key on my keyboard to do these


&#9679; the trick with [Set Composition Key]("http://www.ohbuntu.blogspot.co.uk/2010/02/quickly-type-special-characters-ubuntu.html")i am on Gnome so:

> 
Go to System > Preferences > Keyboard
Select Layout tab
Click on Layout Option
Click Compose Key position
Tick any key you want to assign as Compose Key ( in my case : Right Alt key - image )
Assign Compose Key

How to use?

Press 2 combination key after Compose Key
 example : © ( Copyright sign )
Press & release Compose Key ( in my case : Right Alt key )
Press o key
Then press c key
 [ compose key + o + c = © ]
 Special character © should appear

works a treat for accents and copyright  [SIZE="3"]éá©&#8532;  &#8536; ç ú[/SIZE]  but for a superscript 5 it does not as ^ is already a combination key [shift+6] on my UK keyboard so   unless i misundertood the explanation   it leaves you with nothing unfortunately  : 5 then [shift+6] does not produce anything


 &#9679; shragge thanx this works


> eval echo \$\'\\u207{4..9}\'

  123 done with Alt+ Gr  last six numbers normal to show scale


> [SIZE="2"]¹²³&#8308;&#8309;&#8310;&#8311;&#8312;&#8313;   012345  [FONT="Lucida Sans Unicode"] ¹²³&#8308;&#8309;&#8310;&#8311;&#8312;&#8313;  012345[/FONT][/SIZE]

 that is pretty good   any way to add 0 to this?



Any more ideas anyone?

---

### Post by schragge on 2013-02-27
> **shantiq said:**
> but not quite the same in size if you see    123 done with Alt+ Gr  last six normal to show scale
Well, this probably means that the font your terminal uses only has superscript digits 1 to 4, the rest get completed from another, fallback font. Also, see [here](http://en.wikipedia.org/wiki/Unicode_input#In_X11_.28Linux_and_other_Unix_variants.29) for other input methods.

---

### Post by schragge on 2013-02-27
> **shantiq said:**
> any way to add 0 to this?
```

echo $'\u2070'

```

---

### Post by shantiq on 2013-02-27
--thanx again--



this thread easy to find again by entering ¹²³ in search...

---

### Post by t3chn0k on 2013-05-28
You can type **SHIFT** + **^**&#8203; then write any number from 0 to 9, it will write &#8304;¹²³&#8308;&#8309;&#8310;&#8311;&#8312;&#8313;.

---

### Post by shantiq on 2013-05-28
well [t3chn0k]("http://ubuntuforums.org/member.php?u=1816011")

does not seem to work here on my keyboard  SHIFT + ^&#8203;  produces ^

^ is on top of 6  on my keyboard [UK keyboard]

---

### Post by lykwydchykyn on 2013-05-28
> **shantiq said:**
> well [t3chn0k]("http://ubuntuforums.org/member.php?u=1816011")

does not seem to work here on my keyboard  SHIFT + ^&#8203;  produces ^

^ is on top of 6  on my keyboard [UK keyboard]

You need to hit the compose key first, then you enter the ^ and the number.  But just like alt-gr, it's just another method of entering a unicode character, which may or may not be supported in the font you're using.  A superscript style is probably a safer bet in LibreOffice documents.

---

### Post by Libervurto on 2013-07-18
When typing superscript numbers with the compose key you must type the caret (^) first: ¹²³&#8308;&#8309;&#8310;&#8311;&#8312;&#8313;&#8304;
Typing the number first produces: ¹²³&#8308;&#8309;&#8310;^^°

x° = x degrees = x &#8594; <COMPOSE> &#8594; 0 &#8594; ^
x&#8304; = x^0 = x &#8594; <COMPOSE> &#8594; ^ &#8594; 0

---

