---
title: "Fonts for unicode?"
date: 2012-04-17
forum: The Cafe
---

### Post by iamanidiot123 on 2012-04-17
Which built in font, if any, can render every character in unicode? And, if there are no builtin fonts that can do this, where is there a font that can do this?

---

### Post by grahammechanical on 2012-04-18
Built into where? What program do you want to use these fonts in?

Libreoffice uses unicode fonts. Load Libreoffice Writer, go to the Insert menu and select Insert Special Character. From the dialogue box select a font and then scroll down the panel to see if the font has what you want. You can also choose a Subset of the font as a shortcut to the section where the characters of the subset are.

This might help you in your search:

[http://en.wikipedia.org/wiki/List_of_Unicode_characters]("http://en.wikipedia.org/wiki/List_of_Unicode_characters")

Having a Unicode font with the characters that you want is only one part of the answer. You also need a keyboard layout to access those characters. In Ubuntu we can add keyboard layouts and switch between them.

See System Settings>Keyboard Layout.

By the way, I would not expect to see in a font music notation characters if that font was part of the default set of fonts for a Word processor, even though I see that music notation characters are part of the Unicode specification.



Regards.

---

### Post by gosocial on 2012-04-21
> **grahammechanical said:**
> Built into where? What program do you want to use these fonts in?

Libreoffice uses unicode fonts. Load Libreoffice Writer, go to the Insert menu and select Insert Special Character. From the dialogue box select a font and then scroll down the panel to see if the font has what you want. You can also choose a Subset of the font as a shortcut to the section where the characters of the subset are.

This might help you in your search:

[http://en.wikipedia.org/wiki/List_of_Unicode_characters](http://en.wikipedia.org/wiki/List_of_Unicode_characters)

Having a Unicode font with the characters that you want is only one part of the answer. You also need a keyboard layout to access those characters. In Ubuntu we can add keyboard layouts and switch between them.

See System Settings>Keyboard Layout.

By the way, I would not expect to see in a font music notation characters if that font was part of the default set of fonts for a Word processor, even though I see that music notation characters are part of the Unicode specification.



Regards.
I have some problem with adding currencies with this font.Looking for some concrete solution.

---

### Post by urukrama on 2012-04-21
I don't know what your needs are, but Gentium might be complete enough for your needs. I don't know of any font that has *all* unicode characters.

> Gentium is a typeface family designed to enable the diverse ethnic groups around the world who use the Latin, Cyrillic and Greek scripts to produce readable, high-quality publications. It supports a wide range of Latin- and Cyrillic-based alphabets.

See [http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=Gentium](http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=Gentium)

It is in the repositories as fonts-sil-gentium

---

### Post by MisterGaribaldi on 2012-04-21
Personally, my keyboard layout of choice for Linux is US International AltGR Dead Keys. It works in a very similar (though somewhat more comprehensive) way to how Mac OS X (or even iOS with an external keyboard) does for inserting all kinds of characters.

However, if you're worried about Unicode, I'm assuming you mean non-Western characters. If that's the case, it's not going to matter, you'll need to go hunting manually through the character viewer to find the one(s) you're looking for.

---

