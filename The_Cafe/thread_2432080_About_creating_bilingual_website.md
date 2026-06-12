---
title: "About creating bilingual website"
date: 2019-11-26
forum: The Cafe
---

### Post by satimis on 2019-11-26
Hi,

Please advise which will be an easy way creating a bilingual website based on my running English website.  I'll do the translation myself.  On Internet I found many suggestions.

Thanks in advance.

Regards
satimis

---

### Post by SeijiSensei on 2019-11-27
Usually you'd just duplicate the content in the other language and include a link on each version's page to the other set of pages.  Something like
```

<VirtualHost:80>
stuff
Redirect / https://example.com/en/   <== makes English the default

Alias /en/ /path/to/the/english/directory/
<Directory /path/to/the/english/directory>
stuff
</Directory>

Alias /jp/ /path/to/the/japanese directory/
<Directory /path/to/the/japanese/directory>
stuff
</Directory>

</VirtualHost>

```

---

### Post by sdsurfer on 2019-11-27
What you are likely looking for instead of just translation is* localization*, known as i18n or i10n. It's not usually enough to just translate the words, there are cultural references and context which really change the meaning of word arrangement.

Any way you slice it, to do it correctly it's going to be a lot of tedious stuff. I'm really interested in this topic too as I have some potential translation projects on the table.

A down-and-dirty application used to be the Google Translate tool, which has it's issues (e.g., you just have to hope that G gets it right, and now you are coupled to their service) but that is no longer an option, they are eliminating it.

A second down-and-dirty is to create your own dictionaries and do some sort of specific term translation everywhere on your site. This is a poor solution but it's one I've seen in practice.

```
echo $TranslateClass->translate($lang, 'Term Reference');
```

.... where 'Term Reference' would be defined in all your translation files. You can see the problem. :-) Truthfully, the Wordpress approach is very similar - every output text in a given plugin or theme has a corresponding translation entry. Extremely tedious.

The other and probably most simple is as SijiSensei says, if your content is static and not likely to change, create static versions (and pay a translator to proofread them for you.)

The most robust solutions appear to involve a dictionary framework in one way or another. The dictionary can only be as robust as the definitions you add, most of the time it's a set of phrases and words that translate depending on the language.

If you're using Wordpress, the localization aspect of most of the plugins and themes does exactly that - if the developer has done their work. Very often you can just load a localization files and make the language switch optional, and you're done.

Otherwise it appears (to me) the forerunner is the **GetText()** library which can be implemented in a variety of programming languages, but there's no up-front .po files. You may be able to find **some**, but you'll still have to configure, test, and proofread the results. 

Second up is the ICU project:
[http://site.icu-project.org/](http://site.icu-project.org/)

AFAIK it appears it's only implemented in Java and C/C++.

Would be interested to hear of other options available, this is the extend of what I've found.

---

### Post by satimis on 2019-11-27
Hi all,

Thanks for your advice.

I found an easy way even though you don't speak that language.  It is making use of the online translator (example: Google Language Translate) as plugin to WordPress (I built websites on it)

Steps, please see following video;
How to Add Google Translate in WordPress
[https://www.youtube.com/watch?v=tL8hXYWDS7g](https://www.youtube.com/watch?v=tL8hXYWDS7g)

Example (I just built it):-
Four languages websites;
English
French
Chinese (Simplify and Traditional)
German
[http://diet.reynoldstocks.com/](http://diet.reynoldstocks.com/)

Click [Translate >>] at the center-bottom on each page to popup the country flags and select the language

The disadvantage is the translation being not so typical as made by human.  Besides words on pictures can't be translated

Remark:
======
Where can I add "Solved" to this thread ?

Regards
satimis

---

### Post by yetimon_64 on 2019-11-27
> **satimis said:**
> ...
Remark:
======
Where can I add "Solved" to this thread ?...

From the "Thread Tools" drop down menu at the top of this page in your browser window. There is a link to a guide for how to do so in my signature line if needed, the middle blue link.

Cheers, yeti.

**Edit:** I just noted this post is in the cafe, not in a support area. The [SOLVED] tag possibly may not be used here being a non support area, I am now not sure if it is even available as a result.

---

