---
title: "Selecting the locale to creat a custum CD"
date: 2011-04-27
forum: Ubuntu Translations
---

### Post by PauGNU on 2011-04-27
Hi,

When it comes to Catalan language, there are different variants that can be selected through the language support menu.

We need to prepare a custom Ubuntu cd that uses by default one of those variants identified by the locale: ca_ES.utf8@valencia

On Maverick we added three lines to the /etc/environment file:
LANG=ca_ES.utf8@valencia
LANGUAGE=ca_ES.utf8@valencia
LC_ALL=ca_ES.utf8@valencia

And it worked fine: the custom cd installed ubuntu showing the translation for this variant.

But on natty this doesn't work anymore. I'm using the Ubuntu Customization Kit to do so. I have also tried opening the language support dialog on the UCK and selecting the specific locale, but it doesn't work either.

How can I set this locale and show it by default after installing this custom cd?

Thanks,

Pau

---

