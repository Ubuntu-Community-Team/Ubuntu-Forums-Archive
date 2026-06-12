---
title: "Sanskrit input (Devanagari and transliteration)"
date: 2007-12-20
forum: Tutorials
---

### Post by amerikkanu on 2007-12-20
[COLOR="Red"]**Update**[/COLOR]:  In the new releases since this post was written, Ubuntu has come a very long way with preconfiguring the input method editor, now ibus (formerly SCIM), for us.  It is now ready to go practically out of the box and setting up phonetic &#2342;&#2375;&#2357;&#2344;&#2366;&#2327;&#2352;&#2368; and Transliteration inputs is a trivial affair.  For phonetic Devan&#257;gar&#299;, all you need to do is: 
[LIST=1]
[*] Go to **System > Administration > Language Support**, and in the Language Tab select **ibus** for your "Keyboard Input Method System"
[*] Then click the button **Install / Remove Languages...**, click **Hindi** and **Apply Changes**
[/LIST]

That's it -- too simple!  You may need to log out and log back in (i.e., restart X) for ibus to work.  Once you hit ctrl-space, the ibus daemon should start up and you can begin typing in Devanagari by adding the Hindi Itrans input to your keyboard switcher.  I'll leave the now-obsolete steps previously required for SCIM configuration in a quote below for those on older versions of Ubuntu (or other varieties of Debian), for the sake of reference.  Scroll down below the quote for specific instructions on my recommendations for better Sanskrit input.

> For anyone having difficulty setting up their system to handle Sanskrit input, I'd like to point you to the relevant documentation and provide a few tips to save you a few hours of googling and trial and error.  General disclaimer:  I am still a linux beginner and I've never written an official "tips and tricks" post before, so 1. caveat emptor and 2. all suggestions / feedback / improvements welcome!

**Devanagari** - &#2342;&#2375;&#2357;&#2344;&#2366;&#2327;&#2352;&#2368;

This has worked well in Ubuntu for some time now, it just requires a little system configuration (less now than previously).  Before beginning, you might want to check out the SCIM documentation for Ubuntu [here]("http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu") and [here]("http://www.scim-im.org/wiki/documentation/installation_and_configuration/all/system_configuration").

[LIST=1]
[*]Go to:  **System > Administration > Language Support**, check the box for **Hindi**, click **Apply** and then the select box for **Enable support to enter complex characters**.  Proceed to Step 2.
  
[LIST=2]
[*]That should have pulled in both the Scim input method editor and the Devanagari fonts packages necessary for unicode input.  For those on other Debian systems, who lack the helpful Ubuntu menu mentioned above, you can manually install the packages with the following:
```
sudo aptitude install ttf-devanagari-fonts scim-qtimm scim-tables-additional scim-bridge scim-m17n m17n-lib-bin m17n-db scim-bridge-client-qt4 skim im-switch
```
[/LIST]
[*]Configure your system by entering the following commands in a terminal (for those not in the US, enter the appropriate language / country codes in place of "en_US"):
```
im-switch -z en_US -s scim
export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=scim
export QT_IM_MODULE=scim
```

Note: A more general alternative to the first command is simply "im-switch -z all_ALL -s scim" which may be preferable depending on your language setup.  Also, it should no longer be necessary, but if in the end SCIM does not work properly at startup, you could also add the last three lines of code above to the .bashrc file in your home directory and restart X.
  
[*]Set up SCIM to run at startup by going to **System > Preferences > Sessions > Startup Program > + Add > Command** and enter ```
scim -d
```
[/LIST]

That should be it for the basic set up.  If you were to restart X or reboot at this point, you should be able to type in Devanagari with ease using ibus / m17n.  However, I would recommend first tweaking your input method, because although the hi-itrans transliteration scheme is by far the most user-friendly of those available (in being relatively phonetic), it has a few problems.  One is that the combination "rh" is designed to yield &#2353;&#2381; rather than &#2352;&#2381;&#2361;&#2381; .  Similarly there is no transliteration for the double da&#7751;&#7693;a (used at the end of stanzas, etc., i.e. &#8212; &#2405; &#8212; requiring that one use the less elegant combination of two da&#7751;&#7693;as &#8212; &#2404;&#2404; .  Also, there are several keystroke combinations in the Itrans scheme which to me at least seem either unintuitive or a little unwieldy:  e.g., "R^i" for &#2315; .

[LIST=1]
[*]Exit ibus (if you've already rebooted) and save a backup of your original input file (in your home directory):
```
cp /usr/share/m17n/hi-itrans.mim ~/
```
[*]then open that file for editing:  type in a terminal 
```
sudo gedit /usr/share/m17n/hi-itrans.mim
```
[*]Overwrite the contents of the file with the quote below.  Select all (**Ctrl-a**) in that file and copy / paste the following quote into the hi-itrans file:

> 
;; hi-itrans.mim -- Hindi input method with ITRANS method
;; Copyright (C) 2003, 2004, 2005
;;   National Institute of Advanced Industrial Science and Technology (AIST)
;;   Registration Number H15PRO112

;; This file is part of the m17n database; a sub-part of the m17n
;; library.

;; The m17n library is free software; you can redistribute it and/or
;; modify it under the terms of the GNU Lesser General Public License
;; as published by the Free Software Foundation; either version 2.1 of
;; the License, or (at your option) any later version.

;; The m17n library is distributed in the hope that it will be useful,
;; but WITHOUT ANY WARRANTY; without even the implied warranty of
;; MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
;; Lesser General Public License for more details.

;; You should have received a copy of the GNU Lesser General Public
;; License along with the m17n library; if not, write to the Free
;; Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA
;; 02111-1307, USA.

(input-method hi itrans)

(description "Hindi input method by ITRANS transliteration.
For the detail of ITRANS, see the page:
  <http://www.aczoom.com/itrans/>
")

(title "&#2325;")

(map
 (starter
  (".") ("~") ("#") ("$") ("^") ("*") ((S-\ )) ((C-@))
  ("0") ("1") ("2") ("3") ("4")
  ("5") ("6") ("7") ("8") ("9")
  ("A") ("C") ("D") ("G") ("H") ("I") ("J") ("K") ("L")
  ("M") ("N") ("O") ("R") ("S") ("T") ("U") ("Y")
  ("a") ("b") ("c") ("d") ("e") ("f") ("g") ("h") ("i")
  ("j") ("k") ("l") ("m") ("n") ("o") ("p") ("q") ("r")
  ("s") ("t") ("u") ("v") ("w") ("x") ("y") ("z"))

 (consonant
  ("k" "&#2325;&#2381;")
  ("kh" "&#2326;&#2381;")
  ("g" "&#2327;&#2381;")
  ("gh" "&#2328;&#2381;")
  ("~N" "&#2329;&#2381;")
  ("c" "&#2330;&#2381;")
  ("ch" "&#2331;&#2381;")
  ("j" "&#2332;&#2381;")
  ("jh" "&#2333;&#2381;")
  ("~n" "&#2334;&#2381;")
  (".t" "&#2335;&#2381;")
  ("T" "&#2335;&#2381;")
  (".th" "&#2336;&#2381;")
  ("Th" "&#2336;&#2381;")
  (".d" "&#2337;&#2381;")
  ("D" "&#2337;&#2381;")
  (".dh" "&#2338;&#2381;")
  ("Dh" "&#2338;&#2381;")
  (".n" "&#2339;&#2381;")
  ("N" "&#2339;&#2381;")
  ("t" "&#2340;&#2381;")
  ("th" "&#2341;&#2381;")
  ("d" "&#2342;&#2381;")
  ("dh" "&#2343;&#2381;")
  ("n" "&#2344;&#2381;")
  ("xn" "&#2345;&#2381;")
  ("p" "&#2346;&#2381;")
  ("ph" "&#2347;&#2381;")
  ("b" "&#2348;&#2381;")
  ("bh" "&#2349;&#2381;")
  ("m" "&#2350;&#2381;")
  ("y" "&#2351;&#2381;")
  ("r" "&#2352;&#2381;")
  ("xr" "&#2353;&#2381;")
  ("l" "&#2354;&#2381;")
  ("L" "&#2355;&#2381;")
  ("ld" "&#2355;&#2381;")
  ("v" "&#2357;&#2381;")
  ("w" "&#2357;&#2381;")
  ("sh" "&#2358;&#2381;")
  ("Sh" "&#2359;&#2381;")
  (".s" "&#2359;&#2381;")
  ("s" "&#2360;&#2381;")
  ("h" "&#2361;&#2381;")
  ("q" "&#2392;&#2381;")
  ("K" "&#2393;&#2381;")
  ("xg" "&#2394;&#2381;")
  ("xj" "&#2395;&#2381;")
  ("z" "&#2395;&#2381;")
  (".D" "&#2396;&#2381;")
  (".Dh" "&#2397;&#2381;")
  ("f" "&#2398;&#2381;")
  ("Y" "&#2399;&#2381;")
  ("yh" "&#2399;&#2381;")
  ("GY" "&#2332;&#2381;&#2334;&#2381;")
  ("dny" "&#2332;&#2381;&#2334;&#2381;"))

(independent
("a" "&#2309;")
("aa" "&#2310;")
("A" "&#2310;")
("i" "&#2311;")
("ii" "&#2312;")
("I" "&#2312;")
("u" "&#2313;")
("uu" "&#2314;")
("U" "&#2314;")
(".r" "&#2315;")
("RRi" "&#2315;")
("R^i" "&#2315;")
("LLi" "&#2316;")
("L^i" "&#2316;")
(".l" "&#2316;")
(".c" "&#2317;")
("e.c" "&#2317;")
("E" "&#2318;")
("e" "&#2319;")
("ai" "&#2320;")
("o.c" "&#2321;")
("O" "&#2322;")
("o" "&#2323;")
("au" "&#2324;")
("RRI" "&#2400;")
("R^I" "&#2400;")
(".R" "&#2400;")
("LLI" "&#2401;")
("L^I" "&#2401;")
(".L" "&#2401;")
(".N" "&#2305;")
(".m" "&#2306;")
("M" "&#2306;")
("H" "&#2307;")
(".a" "&#2365;")
(".h" "&#2381;")
("AUM" "&#2384;")
("OM" "&#2384;")
(".." "&#2404;")
(".," "&#2405;")
("0" "&#2406;")
("1" "&#2407;")
("2" "&#2408;")
("3" "&#2409;")
("4" "&#2410;")
("5" "&#2411;")
("6" "&#2412;")
("7" "&#2413;")
("8" "&#2414;")
("9" "&#2415;")
("#" "&#2381;&#2352;")
("$" "&#2352;&#2381;")
("^" "&#2340;&#2381;&#2352;")
("*" "&#2358;&#2381;&#2352;")
("]" "&#2364;")
((S-\ ) "*")
((C-@) "*"))

(dependent
("a" (delete @-) "")
("aa" (delete @-) "&#2366;")
("A" (delete @-) "&#2366;")
("i" (delete @-) "&#2367;")
("ii" (delete @-) "&#2368;")
("I" (delete @-) "&#2368;")
("u" (delete @-) "&#2369;")
("uu" (delete @-) "&#2370;")
("U" (delete @-) "&#2370;")
("RRi" (delete @-) "&#2371;")
("R^i" (delete @-) "&#2371;")
(".r" (delete @-) "&#2371;")
("LLi" (delete @-) "&#2402;")
("L^i" (delete @-) "&#2402;")
(".l" (delete @-) "&#2402;")
(".c" (delete @-) "&#2373;")
("e.c" (delete @-) "&#2373;")
("E" (delete @-) "&#2374;")
("e" (delete @-) "&#2375;")
("ai" (delete @-) "&#2376;")
("o.c" (delete @-) "&#2377;")
("O" (delete @-) "&#2378;")
("o" (delete @-) "&#2379;")
("au" (delete @-) "&#2380;")
("RRI" (delete @-) "&#2372;")
("R^I" (delete @-) "&#2372;")
(".R" (delete @-) "&#2372;")
("LLI" (delete @-) "&#2403;")
(".L" (delete @-) "&#2403;")
("L^I" (delete @-) "&#2403;"))

 (return
  ((Return)))

 (backspace
  ((BackSpace) (undo))))

(state
 (init
  (starter (pushback 1) (shift intermediate)))

 (intermediate
  (consonant (shift second))
  (independent (shift finish))
  (backspace)
  (return (shift init)))

 (second
  (consonant)
  (dependent (shift finish))
  (backspace)
  (return (shift init)))

 (finish
  (return)
  (t (shift init))))

;; Local Variables:
;; coding: utf-8
;; mode: lisp
;; End:

[*]**Hold back m17n-db**.  One neat trick is to hold back the m17n library package so that it won't update and overwrite your edits (you'll be warned first before dist-upgrades).  To do that, enter in a terminal: ```
echo "libm17n-0 hold" | sudo dpkg --set-selections
``` and upgrades will bypass m17n, thus preserving your edits.  If you opt not to hold that file, you'll just need to repeat the two steps above after updates to m17n to restore a more phonetic input in hi-itrans.  For more information on holding and releasing packages, see [here]("https://help.ubuntu.com/community/AptGet/Howto"). 
[*]You should feel free, btw, to tweak the above keyboard map to your tastes, just be sure not to create any conflicts in the process!
[/LIST]

**Reboot** for your changes to take effect and then configure ibus as necessary using "ibus Preferences" and select "hi-itrans" for phonetic Devanagari input.  You can then select from among your newly installed Devanagari fonts (AksharYogini, Chandas, Gargi, Kalimati, Nakula, Sahadeva, Samanata and Sarai).  For a very readable font with a decent set of ligatures, I like Kalimati, though for Sanskrit I tend to use Chandas/Uttara because of its unparalleled ligature set. 


**Transliteration**

Unlike Devanagari, there seems to be a relative dearth of information available for an intuitive system-wide Sanskrit transliteration input method.  I have now found several different ways of going about this, two of which are listed below:  **ibus/m17n** or **Xmodmap**.  I highly recommend the first alternative.

_1st Alternative: ibus/m17n_

The best way to enable an inutitive Sanskrit transliteration input method is to create a new one using ibus/m17n.  The pdf referred to above has the necessary documentation.  I will describe my setup below, by way of example.  [COLOR="Red"]**Update**[/COLOR]:  I have updated this transliteration scheme to include the diacritics necessary for easy inputting of French and German as well.  The hotkeys for those, as well as for the Sanskrit diacritics, may be easily gleaned by referring to the keymap in the quote below.

[LIST=1]
[*]Exit ibus.
[*]Create a new input method file, e.g., ```
sudo gedit /usr/share/m17n/sa-translit.mim
```
and enter the appropriate file preamble and desired keystroke combinations.  The following is the complete content of my file which can be easily copied and pasted and tweaked according to your taste.  Save it, before closing the file:
> ;;; <li> ;;; <li> sa-translit.mim
;;;
;;; Input method for Sanskrit transliteration using the ITRANS scheme.

(title "sa-translit")

(map
(trans

("aa" "&#257;")
("AA" "&#256;")
("ii" "&#299;")
("$e" "&#275;")
("$o" "&#333;")
("II" "&#298;")
("uu" "&#363;")
("UU" "&#362;")
("$E" "&#274;")
("$O" "&#332;")
(".r" "&#7771;")
(".R" "&#7770;")
(".rr" "&#7773;")
(".RR" "&#7772;")
(".l" "&#7735;")
(".L" "&#7734;")
(".ll" "&#7737;")
(".LL" "&#7736;")
(".M" "&#7745;")
(".m" "&#7747;")
(".h" "&#7717;")
(".H" "&#7716;")
(";n" "&#7749;")
(";N" "&#7748;")
("~n" "ñ")
("~N" "Ñ")
(".t" "&#7789;")
(".T" "&#7788;")
(".d" "&#7693;")
(".D" "&#7692;")
(".n" "&#7751;")
(".N" "&#7750;")
(";s" "&#347;")
(";S" "&#346;")
(".s" "&#7779;")
(".S" "&#7778;")
("!a" "à")
("!e" "è")
("!i" "ì")
("!o" "ò")
("!u" "ù")
("!A" "À")
("!E" "È")
("!I" "Ì")
("!O" "Ò")
("!U" "Ù")
("?a" "á")
("?e" "é")
("?i" "í")
("?o" "ó")
("?u" "ú")
("?A" "Á")
("?E" "É")
("?I" "Í")
("?O" "Ó")
("?U" "Ú")
("^a" "â")
("^e" "ê")
("^i" "î")
("^o" "ô")
("^u" "û")
("^A" "Â")
("^E" "Ê")
("^I" "Î")
("^O" "Ô")
("^U" "Û")
("#a" "ä")
("#e" "ë")
("#i" "ï")
("#o" "ö")
("#u" "ü")
("#A" "Ä")
("#E" "Ë")
("#I" "Ï")
("#O" "Ö")
("#U" "Ü")
("%a" "&#259;")
("%i" "&#301;")
("%u" "&#365;")
("%e" "&#277;")
("%o" "&#335;")
("%A" "&#258;")
("%I" "&#300;")
("%U" "&#364;")
("%E" "&#276;")
("%O" "&#334;")
("~a" "ã")
("~i" "&#297;")
("~u" "&#361;")
("~e" "&#7869;")
("~o" "õ")
("~A" "Ã")
("~I" "&#296;")
("~U" "&#360;")
("~E" "&#7868;")
("~O" "Õ")
("-ae" "æ")
("-Ae" "Æ")
("-AE" "Æ")
("-oe" "&#339;")
("-Oe" "&#338;")
("-OE" "&#338;")
(",c" "ç")
(",C" "Ç")
))

(state
(init
(trans)))  
[*]Enter the name of our new input file in the m17n database file.
[LIST=2]
[*]In a terminal enter ```
sudo gedit /usr/share/m17n/mdb.dir
```
[*]change the following lines
> (input-method * "*.mim")
;;; </ul>

to read
> (input-method * "*.mim")
(input-method t sa-translit "sa-translit.mim")
;;; </ul>
[*]Save and exit.
[/LIST]
[/LIST]
Simply restart ibus or if that fails, restart X or reboot.  Your new transliteration input method should be available under the "Other" category of ibus' drop-down menu.

_2nd Alternative:  XModmap_

If for whatever reason, you need another method for transliteration, you can use XModmap.  I've given instructions for that [here]("http://ubuntuforums.org/showthread.php?t=585466&highlight=sanskrit").  This method uses less convenient dead keys, however, and is not convienently switchable, unlike m17n.

I hope this post is of use to others in need of Devanagari and transliterated input on linux.

&#2358;&#2369;&#2349;&#2306; &#2349;&#2357;&#2340;&#2369; &#2404; &#347;ubha&#7747; bhavatu |

---

### Post by rahul_bhise on 2008-02-28
your post was very helpful to me. it has answered lots of questions and made some new questions
i have 4 type of keyboard layout of Hindi
phonetic
inscript
Remington
and now hi-itrans
but what i was searching is godrej and modular type of keyboard
so should i make *.mim file in /usr/share/m17n with all the characters what i want. 
also there are no phonetic.mim, inscript.mim and remington.mim file in /usr/share/m17n/
but i have Hindi-phonetic.bin  Hindi-inscript.bin and dev.remington.bin file in /usr/share/scim/tables/ could i edit these keyboard to suite my needs as you have done hear

[http://www.dataflow.in/dl/godrej.pdf](http://www.dataflow.in/dl/godrej.pdf)
[http://www.dataflow.in/dl/modular.pdf](http://www.dataflow.in/dl/modular.pdf)

---

### Post by sojusnik on 2009-01-06
Thank you!

---

### Post by MountainX on 2009-02-18
Thank you for this.

FYI, I did not have to do step one.

I simply did this: ```
Go to: System > Administration > Language Support, check the box for Hindi, click Apply and then the select box for Enable support to enter complex characters.
```

I checked afterwards with: ```
dpkg -s ttf-devanagari-fonts
```
It reports: ```
Package: ttf-devanagari-fonts
Status: install ok installed

```

And scim is running after reboot.

Is there still a reason to use this?
```
sudo aptitude install ttf-devanagari-fonts scim-qtimm scim-tables-additional scim-bridge scim-m17n m17n-lib-bin
```

---

### Post by MountainX on 2009-02-18
How do I enter &#2310; in the older vedic style as shown in this document?

[http://www.scribd.com/doc/6057769/Yogasutras]("http://www.scribd.com/doc/6057769/Yogasutras")

Thanks

---

### Post by MountainX on 2009-02-19
> **MountainX said:**
> How do I enter &#2310; in the older vedic style (in unicode)?

It appears that the ancient vedic characters are not part of unicode yet:
[http://sanskritlibrary.org/VedicUnicode](http://sanskritlibrary.org/VedicUnicode)

---

### Post by amerikkanu on 2009-02-19
Thanks a lot for the feedback, I'll edit the post accordingly.

---

### Post by amerikkanu on 2009-02-19
Actually, if you use Uttara from this [site]("http://www.sanskritweb.net/cakram/index.html"), you can get that 'a' vowel-sign, and others.  It's the most full featured &#2344;&#2366;&#2327;&#2352;&#2368; font I know of; it's what I usually use, though I prefer the aesthetics / readability of a couple of others.

---

### Post by MountainX on 2009-02-19
> **amerikkanu said:**
> Actually, if you use Uttara from this [site]("http://www.sanskritweb.net/cakram/index.html"), you can get that 'a' vowel-sign, and others.

Thank you! I had that font on my system, but it was corrupted and I didn't know it. I went to the link you provided and downloaded the font again. I like it a lot. It fits my needs.

And thanks again for such a great and helpful post.

---

### Post by ajitarsh on 2009-03-11
Dear amerikkanu,
Thanks and congrats for this great post.
I have used this method on my several systems, but I have faced some problem in my two laptops. 
In my first laptop, the scim icon shown on top bar and there is a display drop down menu containing different languages and their keyboard layouts. But when I select "hi-trans" from the drop down menu the icon appears on the screen but the keyboard doesn't work accordingly.

In my second laptop, I have installed it and it was working before rebooting. After rebooting, SCIM keyboard icon is shown on top bar but the icon is not displaying the drop down menu while clicking on it.

Please guide me in this regard how to solve the above mentioned problems.
Regards
Ajit...

---

### Post by sojusnik on 2009-03-18
@ amerikkanu

Are you using your method of input also for hindi writing or only for sanskrit? Both are written in devanagari, but the behaviour with ligatures and vowels is a little bit different. For example:

The following word written in Hindi is transcribed as follow:
&#2326;&#2367;&#2396;&#2325;&#2368; = khi&#7771;k&#299; = Window

But when you read this word as it would be written in Sanskrit, the transcription would look different:
&#2326;&#2367;&#2396;&#2325;&#2368; = khi&#7771;ak&#299;

Because hindi is only using ligatures for sanskrit words and some other exceptions, most of the hindi words do not have ligatures at all. Additionaly, the vowel a is always added to a consonant in sanskrit, but not in hindi. It's a little bit confusing, but I hope that you know what mean.

Is there a method to configure SCIM for sanskrit and hindi with their special writing rules? How are you handling this problem?

PS: I am using a spaced repetition program to learn vocabulary for hindi and sanskrit. When typing an answer in devanagari, i see dotted circles after signs that have to be ligatures and signs with vowels. How do I get rid of this circles, so that my answer has the exact look of the requested word?

See pictures for clarification:
[http://www.box.net/shared/s2m5dxpl65](http://www.box.net/shared/s2m5dxpl65)
[http://www.box.net/shared/jkpm0xz3e0](http://www.box.net/shared/jkpm0xz3e0)
[http://www.box.net/shared/czaz2sj9k9](http://www.box.net/shared/czaz2sj9k9) 

Maybe this link will help you: [http://groups.google.com/group/ankisrs/browse_thread/thread/f63989cda4fdb0f3](http://groups.google.com/group/ankisrs/browse_thread/thread/f63989cda4fdb0f3)

Thanks in advance!

---

### Post by amerikkanu on 2009-03-18
I only type in Hindi infrequently, so I've never bothered to use anything but the Sanskrit input.  It's surprising that such a popular spoken language as Hindi doesn't have a more intuitive keyboard.  Being a linux/computing newb, I found it difficult to come up with a perfectly phonetic keyboard for Hindi.  Juggling the rules for halant dropping, consonant conjoining and cons-vowel combination left me with two alternatives:  typing the word-internal (but not word-final) 'a' vowels, but having consonants combine automatically; or not typing 'a' vowels in a word, but needing a dead key to signal a combination of consonants.  Either method is more phonetic than Itrans as it stands (and much better than the rest), but neither is perfect.  The first method, though, is nevertheless pretty similar to the popular IME on Windoze, Baraha, so hopefully it won't disappoint too much.  If it's approved, I'll post a link to the howto here.  Thanks for the feedback.

---

### Post by amerikkanu on 2009-03-18
Ajit, glad to hear this tweak has been helpful to you.  Unfortunately, it seems that a recent update of SCIM is interrupting our input method.  I just tweaked another system with this method and found that SCIM/m17n now wouldn't allow me to create a new file, e.g., hi-sanskrit.mim, so I had to overwrite hi-itrans.mim.  Ubuntu now takes care of a lot of SCIM configuration, and it's conceivable that that may be disrupting some of our previous settings.  You might want to check the environment variables ```
printenv
``` against the SCIM settings specified [here]("https://help.ubuntu.com/community/SCIM").  Also, if you're not already overwriting the hi-itrans file, that would be best (as well as to delete hi-sanskrit or whatever other entry you've added to the m17n database).  Also, I've found that rebooting rather than just restarting X is often necessary to test a configuration, and of course, it's easier to start with the clean slate of a fresh install, if that's possible.  Let us know how the troubleshooting goes and best of luck!  Perhaps the SCIM-walas can help us out....

---

### Post by sojusnik on 2009-03-19
@ amerikannu

Do you know something about this issue?
> 
PS: I am using a spaced repetition program to learn vocabulary for hindi and sanskrit. When typing an answer in devanagari, i see dotted circles after signs that have to be ligatures and signs with vowels. How do I get rid of this circles, so that my answer has the exact look of the requested word?

See pictures for clarification:
[http://www.box.net/shared/s2m5dxpl65](http://www.box.net/shared/s2m5dxpl65)
[http://www.box.net/shared/jkpm0xz3e0](http://www.box.net/shared/jkpm0xz3e0)
[http://www.box.net/shared/czaz2sj9k9](http://www.box.net/shared/czaz2sj9k9)

Maybe this link will help you: [http://groups.google.com/group/ankis...3989cda4fdb0f3](http://groups.google.com/group/ankis...3989cda4fdb0f3)

---

### Post by amerikkanu on 2009-03-19
That looks to me to be a Unicode font issue since those circles are part of those characters, indicating that they are dependent ones, allowing IMEs to easily combine characters correctly.  You might want to consult unicode font sites to inquire about that.

---

### Post by sojusnik on 2009-03-20
Hmm, I can't really help myself with this unicode font issue.

Would you mind to install this program and have a quick look yourself.

Download a .deb package here: [http://ichi2.net/anki/download/index.html](http://ichi2.net/anki/download/index.html)

A deck: [http://www.box.net/shared/cqtdf7ou89](http://www.box.net/shared/cqtdf7ou89)

Simply load the deck with this program and type the answer in devanagari.

Thank you.

---

### Post by amerikkanu on 2009-03-22
From what I can see, this is not a SCIM/m17n issue, both of which do their job in inputting the Devanagari properly.  Your program, Anki, however, is then separating characters without regard for the way in which the script is written -- which is *syllabically*.  The Devanagari unicode fonts are smartly designed to produce syllables from individual characters, which is why you see circles where the Anki program has broken a syllable.  "Syllable" for the purposes of the script = either (1) an independent Vowel, or (2) Consonant(s) + a dependent Vowel.  Hence, when Anki breaks up conjunct consonants or separates dependent vowels from the preceding consonants on which they depend, it is breaking up the unified syllable recognized by the unicode font.  This may be an issue that the Anki developer(s) can configure specifically for Devanagari languages like Hindi/Sanskrit.  If I were you, I would email the developer(s) directly or post your issue on the Anki's forums.  Best of luck!

---

### Post by sojusnik on 2009-03-23
Thanks for your reply.

The new version of Anki, 0.9.9.7., solved this problem.

---

### Post by Ian Clark on 2009-04-21
Hellow I followed the old instructions for 8.04 and they worked, but now I'm using 8.10 and the new instructions, and nothing works.

I see the option "t-hi-sanskrit" on scim, but after choosing it, it stays stuck at "en-ispell", and I can't in fact use any of the options except "eng/keyboard".  This is disturbing because I rely on Chinese input for my job, and I can't even use that now.

edit: undid what was done in tutorial, normal functioning scim is back.

---

### Post by Ian Clark on 2009-04-22
I exited scim and did this, as described [here]("http://thanhsiang.org/faqing/node/109").

"Install the Devanagari fonts package and the packages for the input method editor (SCIM):
```
sudo aptitude install ttf-devanagari-fonts scim-qtimm scim-tables-additional scim-bridge scim-m17n m17n-lib-bin
```
In scim, under Hindi input, choose hi-itrans."

Without the extra configuration, there's no conflicts and scim-m17n works normally in Intrepid.  Just that more awkward system that amerikannu had changed before, but its usable.

---

### Post by sojusnik on 2009-05-02
Hi,

It seems that something has changed in jaunty with SCIM. For example,

sudo gedit /usr/share/m17n/mdb.dir

won't bring the desired effect, because mdb.dir is not located there at all.

Did someone use this tutorial to get the promised results in jaunty?

---

### Post by amerikkanu on 2009-05-08
> **Ian Clark said:**
> I exited scim and did this, as described [here]("http://thanhsiang.org/faqing/node/109").

"Install the Devanagari fonts package and the packages for the input method editor (SCIM):
```
sudo aptitude install ttf-devanagari-fonts scim-qtimm scim-tables-additional scim-bridge scim-m17n m17n-lib-bin
```
In scim, under Hindi input, choose hi-itrans."

Without the extra configuration, there's no conflicts and scim-m17n works normally in Intrepid.  Just that more awkward system that amerikannu had changed before, but its usable.

Thanks for the feedback.  I'm using Debian these days more than Ubuntu and didn't catch this glitch in the Ubuntu update.  I've updated the post to deal with this this new conflict, albeit with a somewhat 'dirty' fix.  You should be able just to edit the hi-itrans file as above for less awkward input.

---

### Post by amerikkanu on 2009-05-08
> **sojusnik said:**
> Hi,

It seems that something has changed in jaunty with SCIM. For example,

sudo gedit /usr/share/m17n/mdb.dir

won't bring the desired effect, because mdb.dir is not located there at all.

Did someone use this tutorial to get the promised results in jaunty?

Hi Sojusnik and thanks for the feedback.  I don't quite understand it, though, since I still see all the same files in that m17n directory.  I've updated this post to deal with the conflict in Jaunty.  You should still be able to set up transliteration the same way.  The database file will be overwritten with m17n updates, but not the keyboard map (sa-translit.mim), so you'll just need to update the mdb.dir file after updates to m17n (and the hi-itrans file if you're using the tweaked file for n&#257;gar&#299;).

---

### Post by sojusnik on 2009-05-08
Hi amerikannu,

I'm sorry for this false alarm.

I did a fresh jaunty installation, then followed your instruction:
> 
Update: Since this post was written, Ubuntu has come a long way with preconfiguring the input method editor, SCIM, for us. It is now ready to go practically out of the box. All you need to do is go to: System > Administration > Language Support, check the box for Hindi, click Apply and then select the box for Enable support to enter complex characters. Click Apply and OK. In a terminal type:
```
sudo aptitude install scim-m17n
```

After this step, I couldn't find any *.mim files and the file mdb.dir. So I checked the recommended packages you mentioned before and installed the following 2 packages:
> m17n-db and m17n-lib-bin

After a restart, finally, I could find and edit *.mim files and the mdb.dir file as suggested in your great instruction.

Works great with jaunty!

---

### Post by amerikkanu on 2009-05-08
> **sojusnik said:**
> Hi amerikannu,

I'm sorry for this false alarm.

I did a fresh jaunty installation, then followed your instruction:


After this step, I couldn't find any *.mim files and the file mdb.dir. So I checked the recommended packages you mentioned before and installed the following 2 packages:


After a restart, finally, I could find and edit *.mim files and the mdb.dir file as suggested in your great instruction.

Works great with jaunty!

Thanks for the feedback!  The packaging seems to have changed from version to version of Ubuntu, and since I just keep updating I didn't notice that.  Updated the post with those packages.  Thanks again!

---

### Post by abhay.patil on 2009-08-11
I am new to Ubuntu and believe I have done everything right to have SCIM installed.  However whenever I choose Hindi or Marathi, my keystrokes yield the following instead of valid devanagari.  Not sure what is amiss. 

à¤¹ à¤¨ 

Can somebody point me to an easy to understand documentation on how to input devanagari fonts.  I was fond of Baraha on Windows.  Can I get a similar method here?

Thanks
Abhay

---

### Post by rahul_bhise on 2009-08-11
> **abhay.patil said:**
> 

à¤¹ à¤¨ 

Abhay

whats wrong with it. they are properly typed
may be you are having a wrong encoding
where are you trying to type?
in firefox change the encoding to unicode utf-8
View>Character Encoding>Unicode(UTF-8)

---

### Post by abhay.patil on 2009-08-11
Thanks, Rahul - but the thing is I can SEE devanagari fonts allright on Web and even in a vi session on a terminal.  My problem is that I can not WRITE devanagari fonts on terminal.  In Openoffice, it is still different.  While I can cut and paste devanagari there - it does not even show garbled text when I try to type in after changing language in SCIM.  I am sure I am missing something very simple - but have no clue what it is.  -Abhay

---

### Post by abhay.patil on 2009-08-12
> **abhay.patil said:**
> Thanks, Rahul - but the thing is I can SEE devanagari fonts allright on Web and even in a vi session on a terminal.  My problem is that I can not WRITE devanagari fonts on terminal.  In Openoffice, it is still different.  While I can cut and paste devanagari there - it does not even show garbled text when I try to type in after changing language in SCIM.  I am sure I am missing something very simple - but have no clue what it is.  -Abhay
It has started working magically! :P:confused:
I am at loss what made it work. I just played with admin->language support and SCIM setup to reinstall Hindi and Marathi.   SCIM is also erratic. (I am on 9.0.4).  Right click sometimes does not show any language. I stated scim daemon again, and it started working. The hi-baraha I got somewhere is working like a charm.  Not sure what I was missing earlier though...

---

### Post by shri_nath on 2009-08-16
Hi Amerikkanu,

I followed your directions for installing m17n (db and the lib) and proper changes to the mim fiels and the mdb&#7693;ir. Everything appears to be fine.

If I type a (ordinary unicode-8 text) document in gedit editor it looks fine. If I open the same text document in the Open Office (character set unicode utf-8, default fonts Times New Roman) then the joined consonants are separated (although with correct halants). If I change the font in the open office from Times New Roman to, say Vedana, it rectified the problem.

The problem in typing new document in devanagari in Open Office is that I do not get the (proper ligatures for the) join of consonants: they stay separated. 

**mr-itrans**
For example with mr-itrans I could get &#2344;&#2366;&#2360;&#2381;&#2340;&#2368; by typing nAstI in gedit
as well as in the Open Office.

**mr-phonetic**
When I changed to the mr-phonetic i just could not get that &#2360;&#2381;&#2340;&#2368; (in the &#2344;&#2366;&#2360;&#2381;&#2340;&#2368;): In the gedit I got something like &#2344;&#2366;&#2360;&#2340;&#2368; and in the Open Office I could not get anything typed after the first letter &#2344; (could not even get that to chaneg to nA) the cursor was just stuck there producing nothing of whatever I typed.

I also prefer the input method like Sanskrit in Baraha (on Windows XP).
How do I get that for the gedit and/or Open Office (on ubuntu) ?

Thanks.



-sn

---

### Post by ajitarsh on 2009-11-29
> **amerikkanu said:**
> Thanks for the feedback!  The packaging seems to have changed from version to version of Ubuntu, and since I just keep updating I didn't notice that.  Updated the post with those packages.  Thanks again!

Hello Dear **amerikkanu**,
I am trying to install it in UBUNTU 9.10, but it gives me the given message when I started SCIM through scim -d.
```
ajit@ajit-desktop:~$ scim -d
Smart Common Input Method 1.4.9

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to load x11 FrontEnd module.
Failed to launch SCIM.
ajit@ajit-desktop:~$
```
I am using your transliteration keyboard since UBUNTU 8.04 but I never face this problem. Even in Jaunty it had worked finely.
Kindly give me some solution for it.

Thanks
Ajit...

---

### Post by ajitarsh on 2009-11-29
Now SCIM has started, but itrans works for only Gedit Text Editor.
It is not working for Openoffice and firefox or any other application.
What should I do?

Thanks
Ajit.

---

### Post by amerikkanu on 2009-11-29
> **shri_nath said:**
> If I open the same text document in the Open Office (character set unicode utf-8, default fonts Times New Roman) then the joined consonants are separated (although with correct halants). If I change the font in the open office from Times New Roman to, say Vedana, it rectified the problem.

The problem in typing new document in devanagari in Open Office is that I do not get the (proper ligatures for the) join of consonants: they stay separated.

I also prefer the input method like Sanskrit in Baraha (on Windows XP).
How do I get that for the gedit and/or Open Office (on ubuntu) ?


Sorry for the delay--I've mostly been on other distros of late and didn't see these replies.  In case anyone else has this issue, it ought to just be an OpenOffice configuration issue.  Under Tools > Options... > Language Settings / Default languages for documents / CTL, select Hindi and under OpenOffice.org Writer / Basic Fonts (CTL), select a good unicode Devan&#257;gar&#299; font like Uttara or Sanskrit 2003, etc.  Then, once you restart, OOo intelligently switches between fonts when you switch between input methods.

Regarding Baraha, you're free to tweak the input to bring it more into line with Baraha's character map.  Not being a Windows user any more, I can't help you with that offhand.  I'll try to look into it and post something.

---

### Post by saurabhgeo on 2010-05-11
How do i enter the characters I mean if i want to type &#2367; and then &#2340; this circle after eee is not disappearing .

Any suggestions ?

---

### Post by MountainX on 2010-05-11
> **saurabhgeo said:**
> How do i enter the characters I mean if i want to type &#2367; and then &#2340; this circle after eee is not disappearing .

Any suggestions ?
try typing the chars in the other order

---

### Post by saurabhgeo on 2010-05-11
thanks for quick response but i figured out that a few minutes ago :)

still one thing remains 

I typed this 

&#2313;&#2340;&#2367;&#2359;&#2336; &#2332;&#2366;&#2327;&#2352;&#2367;&#2340; &#2346;&#2352;&#2366;&#2346;&#2351; &#2357;&#2352;&#2366;&#2344;&#2367;&#2348;&#2379;&#2343;&#2367;&#2340; 

but what i actually wanted to typed was this the first quote on this page 

[http://www.bhakti-yoga-meditation.com/inspirational-quotes-sanskrit-aim.html](http://www.bhakti-yoga-meditation.com/inspirational-quotes-sanskrit-aim.html)[http://www.bhakti-yoga-meditation.com/inspirational-quotes-sanskrit-aim.html]("http://www.bhakti-yoga-meditation.com/inspirational-quotes-sanskrit-aim.html")

So how do i make my &#2340; half and other stuff 

I have ubuntu 9.10 and have devnagari keyboard layout option and switch to it to type in devnagari script

---

### Post by leonardo_neo on 2010-09-09
XlitHindi is a plugin for OpenOffice, which is as good as google transliterate IME. Here is the link...

[http://extensions.services.openoffice.org/project/xlithindi]("http://extensions.services.openoffice.org/project/xlithindi")

However, I want to use the transliteration function directly from my keyboard (with ibus). Unfortunately none of the maps are very user friendly for me. I want something like google transliterate. The closest one is "Hindi- Itrans", yet it is not as friendly as google transliterate or XlitHindi. Hope something could be done like this for ibus too.

---

### Post by ajitarsh on 2010-09-09
You can edit the ibus transliteration keymap.
You need to open the keymap file with root user.
For Hindi transliteration you may use this [B]sudo gedit /usr/share/m17n/hi-itrans.mim


[/B]
Now you can edit the key-strokes as you like.
I've edit my keymap as my convenience. You may use it from the given link.
[http://dl.dropbox.com/u/6025645/hi-itrans.mim](http://dl.dropbox.com/u/6025645/hi-itrans.mim)

---

### Post by ganeshbhatbams on 2011-01-14
thank you I have edited harvardkyoto table successfully.
Great post:popcorn:

---

### Post by rahul_bhise on 2012-01-03
> Update: In the new releases since this post was written, Ubuntu has come a very long way with preconfiguring the input method editor, now ibus (formerly SCIM), for us. It is now ready to go practically out of the box and setting up phonetic &#2342;&#2375;&#2357;&#2344;&#2366;&#2327;&#2352;&#2368; and Transliteration inputs is a trivial affair. For phonetic Devan&#257;gar&#299;, all you need to do is:

    Go to System > Administration > Language Support, and in the Language Tab select ibus for your "Keyboard Input Method System"
    Then click the button Install / Remove Languages..., click Hindi and Apply Changes

in ubuntu 11.04 i did not have a m17n folder in /usr/share/
so i added ibus-m17n from ubuntu software center. and i had it
then i clicked on ibus icon in the pannel and go to preference.
in input method tab i added my marathi phonotic input methord and now i can type in marathi.

---

### Post by Abhihemu on 2012-11-19
> **rahul_bhise said:**
> in ubuntu 11.04 i did not have a m17n folder in /usr/share/
so i added** ibus-m17n **from ubuntu software center. and i had it
then i clicked on ibus icon in the pannel and go to preference.
in input method tab i added my marathi phonotic input methord and now i can type in marathi.

It worked for me as well in 10.10, thanks! I had hindi language support installed with some devnagari ttf, it is working very well now.:)
Thanks amerrikannu good info mate!:)

---

### Post by Cnaeus on 2012-12-08
I followed the instructions, but the input method for transliteration didn't appear in ibus.. did something change in Ubuntu 12.04 so that this method doesn't work anymore?

---

### Post by amerikkanu on 2012-12-12
First of all, a big thanks to all of you guys who have helped others to troubleshoot their issues in getting ibus Skt/translit up and running.  I'm on various distros and seem often to get back to this thread after other post-ers have already done the needful.  It's gratifying to see that this thread--five years on!--is still helping people with their setups, due in no small measure to the timely help from all y'all.  So again, many thanks!

@Abhihemu, rahul_bhise, ajitarsh, and ganeshbhatbams:  Glad you guys got everything up and running!  It's useful to know that the instructions still work alright (thanks Abhihemu for that).

@Cnaeus, that's odd, usually transliteration isn't a problem if you've got ibus up and running. Is your ibus working in general (does everything else show up correctly and can you switch between other inputs?).  And does

> (input-method * "*.mim")
(input-method t sa-translit "sa-translit.mim")
;;; </ul> 


show up properly in your database?  You rebooted and started ibus I take it?  All files are in the proper directories?

I'm running 12.04 on one partition and my ibus &#2344;&#2366;&#2327;&#2352;&#2368;/translit system works fine, so that shouldn't be the issue.  Anyway, let us know more specifically what's going on and I'm sure one of us can help you troubleshoot your problem.

---

### Post by Abhihemu on 2012-12-22
> **amerikkanu said:**
> First of all, a big thanks to all of you guys who have helped others to troubleshoot their issues in getting ibus Skt/translit up and running.  I'm on various distros and seem often to get back to this thread after other post-ers have already done the needful.  It's gratifying to see that this thread--five years on!--is still helping people with their setups, due in no small measure to the timely help from all y'all.  So again, many thanks!

@Abhihemu, rahul_bhise, ajitarsh, and ganeshbhatbams:  Glad you guys got everything up and running!  It's useful to know that the instructions still work alright (thanks Abhihemu for that).

....

It's working for me on ubuntu 12.10 as well mate :)

---

