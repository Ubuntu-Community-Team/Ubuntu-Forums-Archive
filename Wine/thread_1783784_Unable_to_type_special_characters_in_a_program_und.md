---
title: "Unable to type special characters in a program under Wine"
date: 2011-06-16
forum: Wine
---

### Post by 3quent on 2011-06-16
Hello, everyone!

I am trying to migrate a couple of PC's in my office to Ubuntu, and I have an old program that's required to run the business (process orders, make invoices).

The program has a Russian interface and the contents of our database are in Latvian (some Latvian words include characters like: &#257; ž &#269; &#326; &#316; &#275; &#299; &#275; &#291;). Thus, to run the program and get a readable interface, the locale in Ubuntu has to be Russian (otherwise it will not run). The program uses a custom font to display Latvian characters, and it works just fine. 

However, I am unable to **input** text with special Latvian characters in this program (the program is called "1C"). 

Strangely, I can type Latvian text in Notepad, but it does not copy into the program's input field.

To enable Latvian input in this program on Windows, a custom dll file should be placed in system32 folder and in the registry, it should be put in place of the "US Dvorak keyboard layout for right hand" dll file. Then, Latvian words could be typed using Dvorak kayboard layout.

I tried it through wine regedit and switched to US Dvorak for right hand in Ubuntu, with no luck.

Has anyone experienced a similar problem? Are there some fonts missing? Maybe wrong locale? 

Thank you.

---

