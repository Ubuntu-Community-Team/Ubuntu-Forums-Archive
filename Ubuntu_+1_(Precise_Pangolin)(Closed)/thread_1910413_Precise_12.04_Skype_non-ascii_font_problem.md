---
title: "Precise 12.04 Skype non-ascii font problem"
date: 2012-01-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-17
I'm having some strange problem with text in Skype. Please look at the screenshot:

[IMG]http://dit.rs/wp-content/uploads/2012/01/skype-font-001.png[/IMG]

Latin ASCII text is displayed correctly, while non-ascii characters are not. Specifically, Cyrillic characters are displayed in a smaller less visible font with Serbian specific Cyrillic characters (&#1113;,&#1114;,&#1112;,&#1106;,&#1115;,&#1119;) being substituted with boxes.

That problem exists in Contacts list, in the messages area (both typing and displaying), Options windows and basically everywhere in Skype where there's any text.

I tried changing the Style option in Skype's General Options, but no result.

Any ideas? Thanks.

---

### Post by GrEEnMK on 2012-03-06
I also have this problem with Skype. Some non-russian cyrillic characters are displayed as boxes [ &#1112; &#1114; &#1113; &#1116; &#1119; &#1109; &#1107; ]

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-06
> **GrEEnMK said:**
> I also have this problem with Skype. Some non-russian cyrillic characters are displayed as boxes [ &#1112; &#1114; &#1113; &#1116; &#1119; &#1109; &#1107; ]

Non-russian Cyrillic letters are not showing because they're missing from the font used to display Cyrillic text. What's bothering me is why is Skype using different fonts to display Latin and non-latin text, even though it is set to use System Defaults. This is very annoying, because the second font is much smaller, and having to guess what letter should stand instead of a box is dumb.

---

### Post by ubudog on 2012-03-06
*Thread moved to Ubuntu +1*

---

### Post by dilshodm on 2012-03-09
Install qt4-qtconfig and set there appropriate font (ex. Ubuntu font) for your qt applications.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-10
dilshodm thanks for the info. I did that, but it didn't work. In qt4-qtconfig Ubuntu font was already selected, and my Skype is still not showing non-ascii characters in Ubuntu font. I even tried using the provided font substitution option, but no luck.

**[SIZE="2"]EDIT: No, I was wrong. Your soultion does work. Exactly what I needed! Why did it take you so long?! ;) Thanks a lot.[/SIZE]**

Also, it was not a good thing to move this thread to Ubuntu+1 section, because it's not a problem specific to Precise. It exists in Oneiric as well, and I only mentioned Precise because that's the version I'm currently using.

---

### Post by Madkinder on 2012-03-20
&#1058;&#1086;&#1084;&#1080;&#1094;&#1072;, what did you actually do to solve the problem? I have exactly the same issue: cyrrilic letters are shown in a weird font. I can read them but they all have different heights and widths.

I installed qt4-config package, launched qtconfig-qt4 and made sure that font named "Ubuntu" is selected. Qtconfig's font preview shows cyrrilic letters in a nice way, but skype seems to completely ignore those settings. What am I doing wrong?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-20
Try restarting Skype. There shouldn't be any tricky parts. I did just what dilshodm said: installed qt4-config, set my font to Ubuntu, style to Medium, size to 11. Oh yeah, and don't forget to **save your settings (ctrl+S) before you close QT4-Config**. Then restart Skype and see if it helps.

---

