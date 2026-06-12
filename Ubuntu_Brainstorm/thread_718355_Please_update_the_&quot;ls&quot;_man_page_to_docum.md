---
title: "Please update the &quot;ls&quot; man page to document the LC_COLLATE variable"
date: 2008-03-08
forum: Ubuntu Brainstorm
---

### Post by ecsd on 2008-03-08
Unless the user sets the LC_COLLATE environmental variable, they can expect strange results from "ls". In particular, ASCII collation is unexpectedly damaged by the system's default and to get "correct" ASCII collation one has to OVERRIDE the system to specify "LC_COLLATE=C" to it.

1. ASCII is an INTERNATIONAL STANDARD and collates in EXACTLY ONE WAY by definition. THIS SHOULD BE THE DEFAULT COLLATION *UNLESS OVERRIDDEN*.

2. Ubuntu appears not to interact with the user to have them set this variable; the user must know to do so. This should be taken care of during setup.

3. The "man" page for "ls" says that output will be alphabetically (read: ascii) sorted by default. The man page says NOTHING about how "alphabetic" is modified by the setting of the LC_COLLATE variable. That is a BUG, since I had to come to this forum to find a cure, instead of just reading the man page and saying "Oh, I see."

4. There is nothing "standard" to my mind of having leading nonalpha characters ignored in a filename sort, nor for case to be ignored (when there are no flags to control case-sorting otherwise.) THOSE BEHAVIORS SHOULD BE NON-DEFAULT and SELECTABLE VIA A FLAG.

The Ubuntu development community, IMO, should respect the fact that half the adoptees of Ubuntu come from the programming/Unix-user world, where the behavior of hundreds of programs is ALREADY WELL UNDERSTOOD. I sggest making the DEFAULT settings those which make Ubuntu COMPATIBLE with other Unixes and then WALK THE USER through things they can change and tailor - so they KNOW WHAT THE DEFAULTS ARE AND KNOW WHAT THEY'VE CHANGED.

I understand that Ubuntu as a whole remains a work in progress, and I hope to see it converge to "all things known and understood". I hope my recommendations will assist in that process.

---

### Post by [h2o] on 2008-03-08
> **ecsd said:**
> 1. ASCII is an INTERNATIONAL STANDARD and collates in EXACTLY ONE WAY by definition. THIS SHOULD BE THE DEFAULT COLLATION *UNLESS OVERRIDDEN*.
Why on earth should that be default? I am quite happy with Ubuntu sorting my file according to my locale (sv_SE.UTF-8 if you wondered)

> 2. Ubuntu appears not to interact with the user to have them set this variable; the user must know to do so. This should be taken care of during setup.No, it is obviously set properly on install to the uses locale.

> The Ubuntu development community, IMO, should respect the fact that half the adoptees of Ubuntu come from the programming/Unix-user world, where the behavior of hundreds of programs is ALREADY WELL UNDERSTOOD. I sggest making the DEFAULT settings those which make Ubuntu COMPATIBLE with other Unixes and then WALK THE USER through things they can change and tailor - so they KNOW WHAT THE DEFAULTS ARE AND KNOW WHAT THEY'VE CHANGED.
Actually, I think very very few Ubuntu users really care of the sort order of ls since most of them will probably never use it.
Really the only time you might need a sorted list is when you _programmatically_ want to go through a list, and most Ubuntu-users are probably never going to do that.

Also, please save the Caps-Lock button from erosion ;)

---

### Post by ecsd on 2008-03-08
Why shouldn't the DEFAULT be the INTERNATIONAL STANDARD? If you don't care, then you shouldn't argue with someone who DOES care.

Quote:
2. Ubuntu appears not to interact with the user to have them set this variable; the user must know to do so. This should be taken care of during setup.
Answer: No, it is obviously set properly on install to the uses locale.

I clearly said there was NO INTERACTION to prompt me to even SET a locale; unless it set "en_US" but STILL gave me a faulty collation. In which case the discrepancy is a BUG.

Answer: Actually, I think very very few Ubuntu users really care of the sort order of ls since most of them will probably never use it.
Really the only time you might need a sorted list is when you _programmatically_ want to go through a list, and most Ubuntu-users are probably never going to do that.

Once again: get it right for the people who DO care. If "only few care" then get it right for THEM. Presumably the rest who don't care, won't care how it comes out.

Ubuntu MUST NOT become a system geared for the explicit use of people who actively wish to know *nothing* before using computers - make something even a fool can use, and only a fool will use it.

ALL CAPS = BOLD and it's faster to type it than try to select what to bold in a window showing me 7-point print. SORRY IF IT BOTHERS YOU.

---

### Post by 23meg on 2008-03-08
Please file a bug report (in the *coreutils* source package), and preferably provide a patch.

---

### Post by [h2o] on 2008-03-08
> **ecsd said:**
> Why shouldn't the DEFAULT be the INTERNATIONAL STANDARD? If you don't care, then you shouldn't argue with someone who DOES care.
Surely, the default should be the locale of whatever locale the user is using? I want to have stuff sorted the way my language does it.
I do however agree that it is a bit strange that "_"-chars and the like are ignored in the sorting though. That might be a bug.

> ALL CAPS = BOLD and it's faster to type it than try to select what to bold in a window showing me 7-point print. SORRY IF IT BOTHERS YOU.
Yes it does. I thought it was common knowledge that writing in CAPS make you seem like you are shouting and is considered rude. Now there's an international standard for you...

---

