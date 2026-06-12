---
title: "Howto get your preferences menu in feisty"
date: 2007-01-17
forum: Ubuntu System Panel
---

### Post by Amaranth on 2007-01-17
This post is really just for the developers but I figured I'm make a new thread to make this information public for everyone.

In GNOME 2.18 (and thus Ubuntu 7.04) we've removed the System->Preferences and System->Administration and settings.menu only has the launcher for GNOME Control Center in it. I'm guessing USP reads settings.menu like alacarte used to to get all the configuration launchers.

To get the launchers that show up in the control center (for access from USP) you need to read preferences.menu instead. This menu has a bunch of submenus defined which are shown as groups in the Control Center. Any item not in one of these submenus is put into an "Other" group in the Control Center. You have the choice of using this grouping in your app or just pulling all the items out of the submenus and presenting a flat list of launchers.

Based on my quick glance at this part of the code I'm going to assume you know how to do all this using gmenu. If not, the following code will get you the flat list of launchers.
```

import gmenu

tree = gmenu.lookup_tree('preferences.menu')

def getLaunchers(parent):
	launchers = []
	#get all children
	for item in parent.get_contents():
		if item.get_type() == gmenu.TYPE_DIRECTORY:
			#item if a submenu, get it's children and add (not append!) them to our list
			launchers += getLaunchers(item)
		else:
			#item is a launcher, append it to our list
			launchers.append(item)
	return launchers

#example usage
for foo in getLaunchers(tree.root):
	print foo.get_name() + ',',

```

Hope this helps, good luck with the rest of the changes you'll need for feisty (like moving to python 2.5).

---

### Post by chanders on 2007-01-17
Hey, glad for you input. Is there somewhere I can go to see the list of changes that were made for Feisty? 

Is there any major change in moving from python 2.4 to 2.5?

Thanks again for your interest and help to the project...

---

### Post by Amaranth on 2007-01-17
You have at lease one place where you reference python2.4 directly. You could avoid this by putting an empty __init__.py file in your usp directory and doing 'from usp import plugins' or whatever. Play around with it, I'm sure you'll figure out how to do what you want. Otherwise I don't think there is anything else special you have to do, the best way to find out is to run usp on feisty. :)

---

### Post by rai4shu2 on 2007-01-17
Nitpick: it's/its in line 10
:)

---

### Post by Malac on 2007-01-17
> **rai4shu2 said:**
> Nitpick: it's/its in line 10
:)
No it's not :)
The items are plural the submenu is singular they belong to it therefore they are it's children. :)
Surely, even more nitpicky.

---

### Post by rai4shu2 on 2007-01-17
It's = contraction of it is
Its = possessive

---

### Post by Malac on 2007-01-17
> **rai4shu2 said:**
> It's = contraction of it is
Its = possessive
No as in,
a runner has shoes, they are the **runner's shoes**. = singular possessive
two runners have shoes they are the **runners' shoes**. = plural possessive
;)

---

### Post by rai4shu2 on 2007-01-17
"It's" is an irregular use of the apostrophe, and as such is used this way:

> No apostrophe is used in the following possessive pronouns and adjectives: yours, his, hers, ours, its, theirs, and whose. (Very many people wrongly use it&#8217;s for the possessive of it; but authorities are unanimous that it&#8217;s can only properly be a contraction of it is or it has.)

[http://en.wikipedia.org/wiki/Apostrophe#Basic_principles:_possessive_apostrophe](http://en.wikipedia.org/wiki/Apostrophe#Basic_principles:_possessive_apostrophe)

---

### Post by Malac on 2007-01-17
> **rai4shu2 said:**
> 
[http://en.wikipedia.org/wiki/Apostrophe#Basic_principles:_possessive_apostrophe](http://en.wikipedia.org/wiki/Apostrophe#Basic_principles:_possessive_apostrophe)
I stand corrected. :oops:
Mind you that's US-English not UK-English :) (Only kidding it's the same in UK-English)

---

### Post by delfick on 2007-01-17
the english language is retarded........

i learnt that in TEE english (f***ing hard subject (western Australian thing).....)

---

### Post by PWill on 2007-01-20
Or we could say "Whoops, Amaranth made a typo. I knew what he was trying to say, so I'm just going to ignore it. He's already doing a nice thing for this project, so I really shouldn't bug him."
/flame

---

