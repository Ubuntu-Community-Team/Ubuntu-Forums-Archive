---
title: "Custom Unicode Character Set"
date: 2009-11-05
forum: The Cafe
---

### Post by Shippou on 2009-11-05
Good day everyone. It's been a while since I logged in and posted here.

I am wondering on how to create a custom character set. I would like for my character set to be publicly distributable.

Basically, I am making a font. But I would like to utilize Unicode's private use area for this, since it can be ported to other machines (am I right about this?).

Any suggestions?

---

### Post by ProgramErgoSum on 2009-11-05
Are you building a character set or fonts ? Unicode knows characters - fonts are anyone's implementation of a given character set codified by (say) Unicode.

---

### Post by simosx on 2009-11-05
Check first at [http://www.unicode.org/charts/](http://www.unicode.org/charts/) if your character set is already defined in Unicode. If it is, then this would make it significantly easier for the users of the font.
If you would like to share what you plan to add, you might get help from this forum.

You can indeed add characters in the Private area. However, your audience will be quite small, and would require to install the font and take special steps so that the characters show up.

---

### Post by Shippou on 2009-11-06
Hello again. Sorry for the very late reply (I currently do not have a dedicated internet connection like I used to have. Pity me...).

I was planning to add the characters in the attached pdf file. 

Yes, I know it seems childish.

What I would like to see is that, for example, when I type "ka", the corresponding character will show up. Something like that.

I know this seems vague, but I can't explain it very much. Sorry.

I like them to be in Unicode because what I plan is I would be able to use them in my Java application (I am currently planning to make a multilingual version of hangman in Java). But I think I have solved the problem (I hope so).

Thank you all for the replies.

P.S. If making a new font is the most feasible way to incorporate these characters, can you suggest a good font editor? I am currently using Windows 7, but, of course, Linux applications are very welcome. I am currently using Puppy Linux 4.4 as my Linux OS. (I would like to reformat my whole hard drive, but since I have no Internet connection, plus my cd burner's broken, things really get challenging here.)

---

### Post by simosx on 2009-11-09
So, here is what you can do.

1. Digimon is an artificial script, which means that currently, it is highly unlikely that it will be included in the Unicode standard. So, the characters need to go to the Private Use Area in Unicode.

2. You need to install Ubuntu; you are in an Ubuntu forum...
Then, go in Applications/Accessories/Character Map and set to view by Unicode block. 
Find the Private Use Area and locate a space there that is not used by other Linux fonts.  The PUA is getting populated with experimental characters from the default fonts in Ubuntu Linux, so your preference would be not to hit on an occupied area. There are a few such areas that can fit the Digimon character set.

3. The tool to use for the script is Fontforge, [http://fontforge.sourceforge.net/](http://fontforge.sourceforge.net/)
It is available in the Ubuntu repositories and you can install from the Software Center.
You would create a new font with the Digimon scripts only. This is fine for Linux. 

4. To test the font, create a subdirectory in your home folder, called ".fonts", and put there your newly created font. It will be picked up automatically by the system and it will appear in Character map.

5. Your last step would be to create a keyboard layout so that you can easily type Digimon. Initially, you can use Character Map to produce Digimon strings.

Good luck!

---

### Post by Shippou on 2009-11-10
Thank you for the mini-tutorial. 

Just one last question though: how can I create a custom keyboard layout? 

I'll try installing Ubuntu ASAP. But then, as I mentioned earlier, I have no dedicated Internet connection, so this would most likely take a while to materialize.

Thank you very much. I really appreciated it.

EDIT: based on the tutorial above, I noticed that making the scripts is much easier using Ubuntu than Windows. Of course, I have to verify it.

---

### Post by simosx on 2009-11-20
There are three ways to make a keyboard layout.
As long as the layout is not complicated, you can use
1. [http://sourceforge.net/projects/duttulm/](http://sourceforge.net/projects/duttulm/)
2. [http://github.com/simos/keyboardlayouteditor](http://github.com/simos/keyboardlayouteditor)
3. do it manually. Edit an existing layout file, found at
/usr/share/X11/xkb/symbols/

For example, in
    key <AC01> {        [         a,    A               ]       }; // a A
you could replace with something like
    key <AC01> {        [      UF021,   UF022           ]       };

---

