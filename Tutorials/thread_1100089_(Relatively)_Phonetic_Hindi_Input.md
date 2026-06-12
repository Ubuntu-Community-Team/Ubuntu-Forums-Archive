---
title: "(Relatively) Phonetic Hindi Input"
date: 2009-03-18
forum: Tutorials
---

### Post by amerikkanu on 2009-03-18
For those who would like a more phonetic Hindi keyboard than is provided by the Phonetic, Itrans or Inscript keyboards in SCIM/M17n, I thought I'd share a couple of tweaks specific to Hindi input.  I previously wrote a howto for Sanskrit input [here]("http://ubuntuforums.org/showthread.php?t=646207"), but obviously it's not ideal for Hindi.  But based on the same setup, I've come up with two alternatives for Hindi.  In both, the final vir&#257;m or halant (&#2381;) is dropped by default from the ends of words.  The first is for folks who still want a somewhat Sanskrit-like input for Hindi, i.e., (1) where you still type every consonant's inherent 'a' (&#2309;) vowel within&#8212;but not at the end of&#8212;a word (e.g., &#2325;&#2352;&#2325;&#2375; = karake) and (2) the conjunct consonants combine automatically (e.g., &#2346;&#2381;&#2352;&#2325;&#2366;&#2358; = prakaash).  The second alternative is for those who would like (1) every consonant's inherent 'a' (&#2309;) vowel to be dropped by default (&#2325;&#2352;&#2325;&#2375; = karke) and (2) for conjunct consonants not to be combined automatically (here the 'w' or another dead key of your choice signals that a consonant should join with the following one, e.g., &#2346;&#2381;&#2352;&#2325;&#2366;&#2358; = wprakaash or wprkaash).  I myself am not a fan of dead keys (like the 'w' in the second method), but I've included it for those who feel that not typing every 'a' within a word is worth typing a 'w' before every conjunct consonant.  You of course can easily further tweak these setups to your liking, just be sure to avoid conflicts (which are not always obvious!).  OK, for the setup:

[LIST=1]
[*]**Install and set up ibus.**  Ubuntu has come a long way with preconfiguring the input method editor, ibus, for us.  It is now ready to go practically out of the box.  All you need to do is go to:  **System > Administration > Language Support**, and in the Language Tab select **ibus** for your "Keyboard Input Method System"
[*] Then click the button **Install / Remove Languages...**, click **Hindi** and **Apply Changes**.  Once ibus/m17n is installed, logout and log back in or reboot, and ibus should be up and running.  There is now a great page for ibus documentation [here]("https://help.ubuntu.com/community/ibus"), which should be your first stop if the above does not get ibus running (with a keyboard on your panel).
[*]**Create a new input file.**
[LIST=1]
[*]Create a new input method file:
```
sudo gedit /usr/share/m17n/hi-itransish.mim
```Choose only one method of input below, select that text and copy it into your new hi-itransish.mim file and save:
[LIST=1]
[*]For those who prefer to type word-internal 'a' vowels and have conjunct consonants (e.g., &#2325;&#2381;&#2359; ) combine automatically, copy and paste the text below, then save and exit:```

;; hi-itransish.mim -- Hindi input method with ITRANS method
;; Copyright (C) 2003, 2004, 2005, 2006, 2007
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
;; Software Foundation, Inc., 51 Franklin Street, Fifth Floor,
;; Boston, MA 02110-1301, USA.

(input-method hi itransish)

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
  ("A") ("C") ("D") ("E") ("G") ("H") ("I") ("J") ("K") ("L")
  ("M") ("N") ("O") ("R") ("S") ("T") ("U") ("Y")
  ("a") ("b") ("c") ("d") ("e") ("f") ("g") ("h") ("i")
  ("j") ("k") ("l") ("m") ("n") ("o") ("p") ("q") ("r")
  ("s") ("t") ("u") ("v") ("w") ("x") ("y") ("z")
  ((KP_1)) ((KP_2)) ((KP_3)) ((KP_4)) ((KP_5))
  ((KP_6)) ((KP_7)) ((KP_8)) ((KP_9)) ((KP_0)))

(consonant
("k" "&#2325;&#2381;")
("kh" "&#2326;&#2381;")
("g" "&#2327;&#2381;")
("gh" "&#2328;&#2381;")
("G" "&#2329;&#2381;")
("c" "&#2330;&#2381;")
("ch" "&#2331;&#2381;")
("j" "&#2332;&#2381;")
("jh" "&#2333;&#2381;")
("~n" "&#2334;&#2381;")
(".t" "&#2335;&#2381;")
(".th" "&#2336;&#2381;")
(".d" "&#2337;&#2381;")
(".dh" "&#2338;&#2381;")
(".n" "&#2339;&#2381;")
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
("xl" "&#2355;&#2381;")
("v" "&#2357;&#2381;")
("sh" "&#2358;&#2381;")
(".s" "&#2359;&#2381;")
("s" "&#2360;&#2381;")
("h" "&#2361;&#2381;")
("q" "&#2392;&#2381;")
("xkh" "&#2393;&#2381;")
("xg" "&#2394;&#2381;")
("xj" "&#2395;&#2381;")
("z" "&#2395;&#2381;")
("x.d" "&#2396;&#2381;")
("x.dh" "&#2397;&#2381;")
("f" "&#2398;&#2381;")
("xy" "&#2399;&#2381;")
("k " "&#2325; ")
("kh " "&#2326; ")
("g " "&#2327; ")
("gh " "&#2328; ")
("G " "&#2329; ")
("c " "&#2330; ")
("ch " "&#2331; ")
("j " "&#2332; ")
("jh " "&#2333; ")
("~n " "&#2334; ")
(".t " "&#2335; ")
(".th " "&#2336; ")
(".d " "&#2337; ")
(".dh " "&#2338; ")
(".n " "&#2339; ")
("t " "&#2340; ")
("th " "&#2341; ")
("d " "&#2342; ")
("dh " "&#2343; ")
("n " "&#2344; ")
("xn " "&#2345; ")
("p " "&#2346; ")
("ph " "&#2347; ")
("b " "&#2348; ")
("bh " "&#2349; ")
("m " "&#2350; ")
("y " "&#2351; ")
("r " "&#2352; ")
("xr " "&#2353; ")
("l " "&#2354; ")
("xl " "&#2355; ")
("v " "&#2357; ")
("sh " "&#2358; ")
(".s " "&#2359; ")
("Sh" "&#2359;&#2381;")
("s " "&#2360; ")
("h " "&#2361; ")
("q " "&#2392; ")
("xkh " "&#2393; ")
("xg " "&#2394; ")
("xj " "&#2395; ")
("z " "&#2395; ")
("x.d " "&#2396; ")
("x.dh " "&#2397; ")
("f " "&#2398; ")
("xy " "&#2399; ")
("j~n " "&#2332;&#2381;&#2334; ")
("GY" "&#2332;&#2381;&#2334;&#2381;")
("GY " "&#2332;&#2381;&#2334; ")
)

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
("^c" "&#2317;")
("e^c" "&#2317;")
("E" "&#2318;")
("e" "&#2319;")
("ai" "&#2320;")
("o^c" "&#2321;")
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
(".`" "&#2381;")
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
("^c" (delete @-) "&#2373;")
("e^c" (delete @-) "&#2373;")
("E" (delete @-) "&#2374;")
("e" (delete @-) "&#2375;")
("ai" (delete @-) "&#2376;")
("o^c" (delete @-) "&#2377;")
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
  (independent (shift init))
  (backspace)
  (return (shift init)))

 (second
  (consonant)
  (dependent (shift init))
  (backspace)
  (return (shift init))))

;; Local Variables:
;; coding: utf-8
;; mode: emacs-lisp
;; End:
```
For those who prefer not to type word-internal 'a' vowels, but use a dead key to form conjunct consonants, copy and paste the text below, then save and exit:```

;; hi-itransish.mim -- Hindi input method with ITRANS method
;; Copyright (C) 2003, 2004, 2005, 2006, 2007
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
;; Software Foundation, Inc., 51 Franklin Street, Fifth Floor,
;; Boston, MA 02110-1301, USA.

(input-method hi itransish)

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
  ("A") ("C") ("D") ("E") ("G") ("H") ("I") ("J") ("K") ("L")
  ("M") ("N") ("O") ("R") ("S") ("T") ("U") ("Y")
  ("a") ("b") ("c") ("d") ("e") ("f") ("g") ("h") ("i")
  ("j") ("k") ("l") ("m") ("n") ("o") ("p") ("q") ("r")
  ("s") ("t") ("u") ("v") ("w") ("x") ("y") ("z")
  ((KP_1)) ((KP_2)) ((KP_3)) ((KP_4)) ((KP_5))
  ((KP_6)) ((KP_7)) ((KP_8)) ((KP_9)) ((KP_0)))

(consonant
("k" "&#2325;")
("kh" "&#2326;")
("g" "&#2327;")
("gh" "&#2328;")
("G" "&#2329;")
("c" "&#2330;")
("ch" "&#2331;")
("j" "&#2332;")
("jh" "&#2333;")
("~n" "&#2334;")
(".t" "&#2335;")
(".th" "&#2336;")
(".d" "&#2337;")
(".dh" "&#2338;")
(".n" "&#2339;")
("t" "&#2340;")
("th" "&#2341;")
("d" "&#2342;")
("dh" "&#2343;")
("n" "&#2344;")
("xn" "&#2345;")
("p" "&#2346;")
("ph" "&#2347;")
("b" "&#2348;")
("bh" "&#2349;")
("m" "&#2350;")
("y" "&#2351;")
("r" "&#2352;")
("xr" "&#2353;")
("l" "&#2354;")
("xl" "&#2355;")
("v" "&#2357;")
("sh" "&#2358;")
(".s" "&#2359;")
("Sh" "&#2359;")
("s" "&#2360;")
("h" "&#2361;")
("q" "&#2392;")
("xkh" "&#2393;")
("xg" "&#2394;")
("xj" "&#2395;")
("z" "&#2395;")
("x.d" "&#2396;")
("x.dh" "&#2397;")
("f" "&#2398;")
("xy" "&#2399;")
("j~n" "&#2332;&#2381;&#2334;")
("GY" "&#2332;&#2381;&#2334;")
("wk" "&#2325;&#2381;")
("wkh" "&#2326;&#2381;")
("wg" "&#2327;&#2381;")
("wgh" "&#2328;&#2381;")
("wG" "&#2329;&#2381;")
("wc" "&#2330;&#2381;")
("wch" "&#2331;&#2381;")
("wj" "&#2332;&#2381;")
("wjh" "&#2333;&#2381;")
("w~n" "&#2334;&#2381;")
("w.t" "&#2335;&#2381;")
("w.th" "&#2336;&#2381;")
("w.d" "&#2337;&#2381;")
("w.dh" "&#2338;&#2381;")
("w.n" "&#2339;&#2381;")
("wt" "&#2340;&#2381;")
("wth" "&#2341;&#2381;")
("wd" "&#2342;&#2381;")
("wdh" "&#2343;&#2381;")
("wn" "&#2344;&#2381;")
("wxn" "&#2345;&#2381;")
("wp" "&#2346;&#2381;")
("wph" "&#2347;&#2381;")
("wb" "&#2348;&#2381;")
("wbh" "&#2349;&#2381;")
("wm" "&#2350;&#2381;")
("wy" "&#2351;&#2381;")
("wr" "&#2352;&#2381;")
("wxr" "&#2353;&#2381;")
("wl" "&#2354;&#2381;")
("wxl" "&#2355;&#2381;")
("wv" "&#2357;&#2381;")
("wsh" "&#2358;&#2381;")
("w.s" "&#2359;&#2381;")
("wSh" "&#2359;&#2381;")
("ws" "&#2360;&#2381;")
("wh" "&#2361;&#2381;")
("wq" "&#2392;&#2381;")
("wxkh" "&#2393;&#2381;")
("wxg" "&#2394;&#2381;")
("wxj" "&#2395;&#2381;")
("wz" "&#2395;&#2381;")
("wGY" "&#2332;&#2381;&#2334;&#2381;")
("wx.d" "&#2396;&#2381;")
("wx.dh" "&#2397;&#2381;")
("wf" "&#2398;&#2381;")
("wxy" "&#2399;&#2381;"))

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
(".l" "&#2316;")
("^c" "&#2373;")
("e^c" "&#2317;")
("E" "&#2318;")
("e" "&#2319;")
("ai" "&#2320;")
("o^c" "&#2321;")
("O" "&#2322;")
("o" "&#2323;")
("au" "&#2324;")
("RRI" "&#2400;")
("R^I" "&#2400;")
(".R" "&#2400;")
(".L" "&#2401;")
(".N" "&#2305;")
(".m" "&#2306;")
("M" "&#2306;")
("H" "&#2307;")
(".a" "&#2365;")
(".`" "&#2381;")
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
("a" "")
("aa" "&#2366;")
("A" "&#2366;")
("i" "&#2367;")
("ii" "&#2368;")
("I" "&#2368;")
("u" "&#2369;")
("uu" "&#2370;")
("U" "&#2370;")
("RRi" "&#2371;")
("R^i" "&#2371;")
(".r" "&#2371;")
(".l" "&#2402;")
("^c" "&#2373;")
("E" "&#2374;")
("e" "&#2375;")
("ai" "&#2376;")
("o^c" "&#2377;")
("O" "&#2378;")
("o" "&#2379;")
("au" "&#2380;")
("RRI" "&#2372;")
("R^I" "&#2372;")
(".R" "&#2372;")
(".L" "&#2403;"))
 (return
  ((Return)))

 (backspace
  ((BackSpace) (undo))))

(state
 (init
  (starter (pushback 1) (shift intermediate)))

 (intermediate
  (consonant (shift second))
  (independent (shift init))
  (backspace)
  (return (shift init)))

 (second
  (consonant)
  (dependent (shift init))
  (backspace)
  (return (shift init))))

;; Local Variables:
;; coding: utf-8
;; mode: emacs-lisp
;; End:

```
[/LIST]
[/LIST]  
[*]Update the m17n database.[LIST=1]
[*]Open the database file:```
sudo gedit /usr/share/m17n/mdb.dir
```
[*]Replace the following code```

(input-method * "*.mim")
;;; </ul>

```
with
```
(input-method * "*.mim")
(input-method t hi-itransish "hi-itransish.mim")
;;; </ul>

```
[*]Save and exit the mdb.dir file.
[/LIST]
[*]**Hold back m17n-db**.  One neat trick is to hold back the m17n database package so it won't update and overwrite your edits (you'll be warned first before dist-upgrades).  To do that, enter in a terminal: ```
echo "m17n-db hold" | sudo dpkg --set-selections
``` and upgrades will bypass m17n, thus preserving your edits.  If you opt not to hold that file, you'll just need to repeat the steps above after updates to m17n to show the m17n-db file your hi-itransish.mim file.  For more information on holding and releasing packages, see [here]("https://help.ubuntu.com/community/AptGet/Howto"). 
[*]**Reboot** for your changes to take effect and then configure ibus as necessary using "ibus Setup."
[/LIST]
That's it, &#2358;&#2366;&#2348;&#2366;&#2358;!  You should now have a relatively more phonetic Hindi keyboard at your disposal.  Please do post feedback on this howto so I can correct / update the post and help troubleshoot any problems.  I am a linux newb btw, so if there's anything I'm missing here, please feel free to point it out.  Thanks.

---

### Post by harsh1kumar on 2009-04-11
&#2309;&#2330;&#2381;&#2331;&#2368; &#2346;&#2379;&#2360;&#2381;&#2335; &#2361;&#2376; &#2404; &#2343;&#2344;&#2381;&#2351;&#2357;&#2366;&#2342; &#2404; :p

---

### Post by naklinaam on 2009-04-20
Great post.. Thanks a ton.

I use the 1st option (explicit a after consonants).

Just have 1 questions.

1. How do I write "Ksh" as in "Kshatriya / Kshama" not looking for &#2325;&#2381;&#2358;.

2. I tried printing a staroffice spreadsheet with Hindi fonts but got only [] kind of boxes instead of the hindi font. I use an HP Laserjet 1018. Do I need to install some additional fonts for the printer?


Added on 21-Apr-2009:
upgrading to ubuntu 9.04 reversed this change for me. I am back to the original itrans file, and I got back my '&#2325;&#2381;&#2359;' :)
#the above post is missing an entry in the consonant section
("x" "&#2325;&#2381;&#2359;&#2381;"). **CAUTION** adding this entry as is will conflict with the entries for &#2394;&#2381;, &#2395;&#2381;, &#2393;&#2381;, &#2345;&#2381; etc. make sure to resolve all conflicts if you are doing it yourself*****

You could probably also add back the 
 ("GY" "&#2332;&#2381;&#2334;&#2381;") as that is how some people type / pronounce &#2332;&#2381;&#2334;.

Can you please still help with printing question?

---

### Post by amerikkanu on 2009-04-21
> **naklinaam said:**
> Great post.. Thanks a ton.

Hi, thanks for the kudos and sorry for the delay...

> I use the 1st option (explicit a after consonants).

Just have 1 questions.

1. How do I write "Ksh" as in "Kshatriya / Kshama" not looking for &#2325;&#2381;&#2358;.

That would be written "k.s" since you need to use a retroflex 's' and I standardized a period for all retroflexes in the character map.  If you want, however, you can simply go into that hi-itrans.mim file and modify your keyboard to suit your taste....

> 2. I tried printing a staroffice spreadsheet with Hindi fonts but got only [] kind of boxes instead of the hindi font. I use an HP Laserjet 1018. Do I need to install some additional fonts for the printer?

You shouldn't need to.  You might want to try the command:

```
sudo apt-get install ttf-devanagari-fonts
``` to make sure that you've got a set of good unicode fonts available.  There shouldn't be any real issues with nagari input in OpenOffice any more.  It's probably just a matter of making sure you've got the right settings at this point -- which ought to be fixable by a visit to OOo's forums and a little googling.  If that doesn't solve it, let me know.  Enjoy!

---

### Post by amerikkanu on 2009-04-21
> **billyg said:**
> Can I use this method for urdu?

&#1705;&#1740;&#1575; &#1605;&#1740;&#1722; &#1575;&#1587; &#1591;&#1585;&#1740;&#1602;&#1746; &#1587;&#1746; &#1575;&#1585;&#1583;&#1608; &#1575;&#1587;&#1578;&#1593;&#1605;&#1575;&#1604; &#1705;&#1585;&#1587;&#1705;&#1578;&#1575; &#1729;&#1608;&#1722;&#1567;

Hi, I take it you've already seen that m17n supports Arabic script input for Urdu.  I don't know enough about that script to say whether it could be similarly tweaked for more phonetic input, sorry.  Since you do know the script, though, you might want to dig around in the relevant files in the m17n directory "/usr/share/m17n/".  Tweaking isn't difficult and the syntax rules are fairly simple to derive.  Best of luck!

---

### Post by sojusnik on 2009-05-04
As mentioned in a related topic: [http://ubuntuforums.org/showthread.php?t=646207&page=3](http://ubuntuforums.org/showthread.php?t=646207&page=3)

the modifications suggested here are not working with SCIM under jaunty jackalope.

Every help appreciated.

---

### Post by amerikkanu on 2009-05-08
> **naklinaam said:**
> Great post.. Thanks a ton.

I use the 1st option (explicit a after consonants).

Just have 1 questions.

1. How do I write "Ksh" as in "Kshatriya / Kshama" not looking for &#2325;&#2381;&#2358;.

2. I tried printing a staroffice spreadsheet with Hindi fonts but got only [] kind of boxes instead of the hindi font. I use an HP Laserjet 1018. Do I need to install some additional fonts for the printer?


Added on 21-Apr-2009:
upgrading to ubuntu 9.04 reversed this change for me. I am back to the original itrans file, and I got back my '&#2325;&#2381;&#2359;' :)
#the above post is missing an entry in the consonant section
("x" "&#2325;&#2381;&#2359;&#2381;"). **CAUTION** adding this entry as is will conflict with the entries for &#2394;&#2381;, &#2395;&#2381;, &#2393;&#2381;, &#2345;&#2381; etc. make sure to resolve all conflicts if you are doing it yourself*****

You could probably also add back the 
 ("GY" "&#2332;&#2381;&#2334;&#2381;") as that is how some people type / pronounce &#2332;&#2381;&#2334;.

Can you please still help with printing question?

Hi and thanks for the feedback.  I was able to get this method working again via a new input file (which I named itransish), so there's no need now for editing the original itrans file -- which will prevent the new file from being overwritten with updates to m17n (though the database file will be, so that will need to be tweaked after updates to m17n).  In doing that, I put a few of the combinations you mentioned back in, where there weren't conflicts:  GY for &#2332;&#2381;&#2334;&#2381;, Sh for &#2359;&#2381; (so that &#2325;&#2381;&#2359; can be written with "kSh" or "k.s").  Unfortunately, I don't know the answer to your printer/Star Office question.  As that problem isn't specific to the tweaks listed here (as evidenced by the fact that it happens with the original itrans file), CUPS, SCIM or Star Office forums ought to be of more help.

---

### Post by amerikkanu on 2009-05-08
> **sojusnik said:**
> As mentioned in a related topic: [http://ubuntuforums.org/showthread.php?t=646207&page=3](http://ubuntuforums.org/showthread.php?t=646207&page=3)

the modifications suggested here are not working with SCIM under jaunty jackalope.

Every help appreciated.
I've gone through this method again on my computer after updating to Jaunty and it works for me.  I don't understand your problem, since all the files are in their same directory on my system.  Did you do a fresh install?

---

### Post by forthe on 2009-05-17
&#2310;&#2346;&#2325;&#2375; &#2342;&#2381;&#2357;&#2366;&#2352;&#2366; &#2348;&#2344;&#2366;&#2351;&#2366; &#2361;&#2369;&#2310; &#2325;&#2368;&#2348;&#2379;&#2352;&#2381;&#2337; &#2348;&#2361;&#2369;&#2340; &#2348;&#2337;&#2367;&#2351;&#2366; &#2361;&#2376;. &#2343;&#2344;&#2381;&#2351;&#2357;&#2366;&#2342; .

&#2325;&#2369;&#2331; changes &#2350;&#2376;&#2344;&#2375;&#2306; &#2325;&#2367;&#2351;&#2375; &#2361;&#2376;&#2306; &#2332;&#2376;&#2360;&#2375; "&#2330;" &#2354;&#2367;&#2326;&#2344;&#2375; &#2325;&#2375; &#2354;&#2367;&#2351;&#2375; "c" &#2325;&#2367; &#2332;&#2327;&#2361; "ch" &#2325;&#2352; &#2342;&#2367;&#2351;&#2366; &#2361;&#2376; &#2324;&#2352; "&#2331;" &#2325;&#2375; &#2354;&#2367;&#2351;&#2375; "chh" &#2332;&#2379; &#2325;&#2368; &#2350;&#2375;&#2352;&#2375; &#2309;&#2344;&#2369;&#2325;&#2370;&#2354; &#2361;&#2376;. &#2311;&#2360;&#2360;&#2375; &#2346;&#2361;&#2354;&#2375; &#2311;&#2340;&#2344;&#2366; &#2309;&#2330;&#2381;&#2331;&#2366; &#2325;&#2368;&#2348;&#2379;&#2352;&#2381;&#2337; &#2350;&#2369;&#2333;&#2375; &#2357;&#2367;&#2344;&#2381;&#2337;&#2379;&#2395; &#2319;&#2325;&#2381;&#2360; &#2346;&#2368; &#2350;&#2375;&#2306; "hindiwriter" &#2344;&#2366;&#2350;&#2325; &#2360;&#2366;&#2398;&#2381;&#2335;&#2357;&#2375;&#2351;&#2352; &#2360;&#2375; &#2350;&#2367;&#2354;&#2366; &#2341;&#2366;. &#2310;&#2346;&#2325;&#2366; &#2313;&#2360;&#2360;&#2375; &#2349;&#2368; &#2309;&#2330;&#2381;&#2331;&#2366; &#2361;&#2376;.

---

### Post by naklinaam on 2009-07-18
@amerikkanu,
Hi, Me again, and once gain, thanks a ton for this great guide.

I used this guide to configure ubuntu 8.10 with a Hindi keyboard and it worked great.

I upgraded to 9.04, and tried the same script and it worked there as well.

However, i did a fresh install of 9.04 recently and have run into some issue

It works great for all keyboards other than 'hi-itrans' (I still followed the old settings).
I have run into a crazy issue. Whenever I select Hindi Itrans from the SCIM list, it remains stuck with the previous selection (English keyboard or Bengali or whatever else I maght have tested with before Hindi). I am also able to invoke hindi Remington etc..
The only keyboard which does not work is the hindi itrans.

Can you please help me get that working? I dont even know what information mighthelp solve it.
The first thing I would like to look at is where do I map the choice I made from the scim panel to the actual file used for that choice. I guess something might be missing there.
Can you please help as this is the only keyboard I really want to use in addition to English.

---

### Post by amerikkanu on 2009-07-30
> **naklinaam said:**
> @amerikkanu,
It works great for all keyboards other than 'hi-itrans' (I still followed the old settings).
I have run into a crazy issue. Whenever I select Hindi Itrans from the SCIM list, it remains stuck with the previous selection (English keyboard or Bengali or whatever else I maght have tested with before Hindi). I am also able to invoke hindi Remington etc..
The only keyboard which does not work is the hindi itrans.


Sorry for the delay, I'm on summer break!  I'm not sure I understand your setup.  Did you create a new itransish input or did you simply tweak the itrans input?  If the latter, you ought to be able to overwrite it with the original from the backup.  If you didn't back it up and there's none automatically saved in its directory, then you could just delete that file (/usr/share/m17n/itrans.mim), remove&purge scim/m17n and reinstall them using the instructions above.  That should give you a clean itrans.mim file.  On the other hand, if you did try to create an itransish.mim file and something went wrong, it could be creating a conflict with the itrans.mim file -- so you'd want in that case to delete both the itransish.mim file and its entry from the m17 db file.

Otherwise, if you haven't already created one, you could simply create the itransish input using the instructions above as a workaround to the itrans input.  I just did so on a fresh install of 9.04 and it works without a hitch.  Good luck and let me know how things go.

---

### Post by swapnil_bhartiya on 2009-08-21
&#2310;&#2349;&#2366;&#2352; &#2354;&#2375;&#2325;&#2367;&#2344; &#2325;&#2369;&#2331; &#2360;&#2350;&#2360;&#2381;&#2351;&#2366; &#2361;&#2376;..&#2346;&#2381;&#2352;&#2325;&#2366;&#2358; &#2325;&#2366; '&#2352;' &#2325;&#2376;&#2360;&#2375; &#2348;&#2344;&#2375;&#2327;&#2366; &#2324;&#2352; &#2309;&#2352;&#2381;&#2343; &#2330;&#2306;&#2342;&#2381;&#2352;&#2348;&#2367;&#2306;&#2342;&#2368;? &#2311;&#2360;&#2368; &#2325;&#2375; &#2360;&#2366;&#2341; '?' &#2325;&#2361;&#2366;&#2305; &#2360;&#2375; &#2348;&#2344;&#2375;&#2327;&#2366;? &#2310;&#2349;&#2366;&#2352;. &#2350;&#2376; &#2313;&#2348;&#2369;&#2344;&#2381;&#2340;&#2369; &#2415;.&#2406;&#2410; &#2325;&#2366; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327; &#2325;&#2352; &#2352;&#2361;&#2366; &#2361;&#2370;&#2305;.

---

### Post by amerikkanu on 2009-08-23
> **swapnil_bhartiya said:**
> &#2310;&#2349;&#2366;&#2352; &#2354;&#2375;&#2325;&#2367;&#2344; &#2325;&#2369;&#2331; &#2360;&#2350;&#2360;&#2381;&#2351;&#2366; &#2361;&#2376;..&#2346;&#2381;&#2352;&#2325;&#2366;&#2358; &#2325;&#2366; '&#2352;' &#2325;&#2376;&#2360;&#2375; &#2348;&#2344;&#2375;&#2327;&#2366; &#2324;&#2352; &#2309;&#2352;&#2381;&#2343; &#2330;&#2306;&#2342;&#2381;&#2352;&#2348;&#2367;&#2306;&#2342;&#2368;? &#2311;&#2360;&#2368; &#2325;&#2375; &#2360;&#2366;&#2341; '?' &#2325;&#2361;&#2366;&#2305; &#2360;&#2375; &#2348;&#2344;&#2375;&#2327;&#2366;? &#2310;&#2349;&#2366;&#2352;. &#2350;&#2376; &#2313;&#2348;&#2369;&#2344;&#2381;&#2340;&#2369; &#2415;.&#2406;&#2410; &#2325;&#2366; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327; &#2325;&#2352; &#2352;&#2361;&#2366; &#2361;&#2370;&#2305;.

&#2325;&#2381;&#2351;&#2366; &#2310;&#2346; &#2344;&#2375; &#2346;&#2381;&#2352;&#2341;&#2350;&#2375; &#2351;&#2366; &#2342;&#2370;&#2360;&#2352;&#2375; &#2357;&#2367;&#2343;&#2367; &#2325;&#2366; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327; &#2325;&#2367;&#2351;&#2366; ?  &#2309;&#2327;&#2352; &#2310;&#2346; &#2344;&#2375; &#2346;&#2381;&#2352;&#2341;&#2350;&#2375; &#2357;&#2367;&#2343;&#2367; &#2325;&#2366; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327; &#2325;&#2367;&#2351;&#2366;, &#2340;&#2379; &#2346;&#2381;&#2352;&#2325;&#2366;&#2358; &#2325;&#2366; '&#2352;&#2381;' &#2309;&#2346;&#2344;&#2375; &#2310;&#2346; &#2348;&#2344;&#2375;&#2327;&#2366; -- &#2350;&#2340;&#2354;&#2348;&#2381;, &#2346;&#2381;&#2352;&#2325;&#2366;&#2358; = prakaash &#2404;  &#2324;&#2352; &#2360;&#2306;&#2346;&#2381;&#2352;&#2340;&#2368;&#2325; &#2325;&#2369;&#2306;&#2332;&#2368; &#2314;&#2346;&#2352; &#2350;&#2367;&#2354;&#2340;&#2368; &#2361;&#2376; &#2404;  &#2340;&#2379;,

&#2305; = .N
&#2306; = .m

&#2309;&#2327;&#2352; &#2310;&#2346; &#2325;&#2375; &#2324;&#2352; &#2360;&#2357;&#2366;&#2354; &#2361;&#2376;&#2306;, &#2340;&#2379; &#2325;&#2371;&#2346;&#2351;&#2366; &#2346;&#2370;&#2331;&#2367;&#2351;&#2375; &#2404;  &#2324;&#2352; &#2350;&#2366;&#2398; &#2325;&#2368;&#2332;&#2367;&#2351;&#2375;, &#2350;&#2375;&#2352;&#2368; &#2361;&#2367;&#2344;&#2381;&#2342;&#2368; &#2319;&#2325;&#2342;&#2350; &#2335;&#2370;&#2335;&#2368;-&#2398;&#2370;&#2335;&#2368; &#2361;&#2379; &#2327;&#2351;&#2368; &#2404; &#2325;&#2367;&#2344;&#2381;&#2340;&#2369; &#2350;&#2369;&#2333;&#2375; &#2310;&#2358;&#2366; &#2361;&#2376; &#2325;&#2367; &#2350;&#2375;&#2352;&#2366; &#2309;&#2352;&#2381;&#2341; &#2360;&#2381;&#2346;&#2359;&#2381;&#2335; &#2361;&#2376; &#2404;  &#2360;&#2380;&#2349;&#2366;&#2327;&#2381;&#2351; &#2361;&#2379; &#2404;

---

### Post by manit on 2010-01-01
I have found out that if you use 'lohit hindi' font then type in hindi then you get what you see.
Actually in my case also initially font was 'dejavu sans' so got boxes on paper printed but then font 'lohit hindi' worked.
Glad to help you.

---

### Post by manit on 2010-01-01
please see above post as I read somebody had problem on first page

---

### Post by bumeshrai on 2011-11-17
I am a south indian trying to type Rail. I am getting  &#2352;&#2375;&#2354;&#2381; instead of  &#2352;&#2375;&#2354;. How do I do it. in phonetic keyboard I am typing "rel" as well as "rel ", with the same result.

---

