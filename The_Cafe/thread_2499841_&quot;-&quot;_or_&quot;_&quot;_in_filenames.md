---
title: "&quot;-&quot; or &quot;_&quot; in filenames?"
date: 2024-08-12
forum: The Cafe
---

### Post by him610 on 2024-08-12
Are there some guidelines on the use of "-" and "_" when developing filenames?

For instance,  *wireless-info* and *wireless-info.txt* both use "-" while *.bash_history* and *.bash_logout* both use "_".

Is there some logic as to which one to use?

---

### Post by TheFu on 2024-08-12
Not that I know.  I use both.

Then there's always **useradd** and **adduser**.  Much clearer, right?  ;)


Some examples, 
```
2024-Olympics-M_3m_Prel-str1080.mkv
2024-Olympics-M_3m_SF-str1080.mkv
2024-Olympics-M_3m_Fin-str1080.mkv
2024-Olympics-M_3m_Sync_Fin-str1080.mkv
```

The media parsers probably don't care, but my brain doesn't see _ like it sees -.  I do the same for TV and ripped movies, just with the  {Title}-{year}-{episode}-{source}.mkv

As for select/paste, X/Windows doesn't seem to care.  Or perhaps it is my terminal?   Doube-click grabs the word (spaces denote a word), triple-click grabs the entire line. Both put them into the X/buffer.  I don't use addon "clipboards". No need. They just get in the way.  No need for "copy" using keyboard or menus either.  Why do things the slow way?

If a Title has a '-' in it, I convert that to an '_' for consistency.

For scripts, it is really 50/50 each way. Don't know why?  I almost never make a script with uppercase unless the purpose of the script is related to something commonly using uppercase.  
```
NASA-KSC-audio
NTFS-250G-Format
```

The NASA-KSC audio script was created about a decade ago.  The NTFS-250G-Format script was created about 4 yrs ago after I got tied of looking up in my vimwiki how to do it.  Scripts where my wiki for decades before I got hooked onto vimwiki.  I have lots of README files in my ~/bin/ and in specific directories as reminders.  They aren't just "README" since those are for packages, but I add other descriptive characters to the filename so I know it is something I've written.

Being able to find the file I need later is what my names are all about.  Normally, I use **locate -ir** for that.

---

### Post by Claus7 on 2024-08-12
Hello,

I suppose that _ is safer since in some cases the - is interpreted differently and might cause issues (size can differ). I think that I came across lately an issue using _ though: copy pasting didn't work, whereas typing it, it was recognized as it should. Nonetheless I still would prefer _.

Regards!

---

### Post by guiverc on 2024-08-13
I recall being told that "-" is invalid on some machines/architectures..  but as more didn't allow "_", being advised to use "-" as it was the more globally acceptable.  Alas I can't recall on what machines/OSes they were, but given this *memory *is probably from three decades ago, its probably worthless today.

I think it'll depend where you trained, and what your background was... just like command options using hypen, no-hypen or double-hypen preferences showing the background of unix, bsd & gnu coders & training I suspect.   Opinion only.

---

### Post by currentshaft on 2024-08-14
-_-

---

### Post by QIII on 2024-08-15
For many, many years I was a software developer, eventually owning a software company.  In the 70s we used underscores.  

Many things have changed.  For one thing, it is now the case that hyphens make for better indexing of web content/resources.  Underscores can confound indexing,

But I disagree that dashes are easier to read -- at least for humans.  Well, maybe just some of us old-timey humans.

---

### Post by him610 on 2024-08-16
> BTW, did you know some systems don’t handle spaces in filenames well
Yes, I was aware of the issue with spaces. That is a good reason for using "-" or "_" in filenames, then there is also the camel method where all the WordsRunTogether with first letter of each word in caps.

---

