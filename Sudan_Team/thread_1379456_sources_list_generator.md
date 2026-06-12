---
title: "sources list generator"
date: 2010-01-12
forum: Sudan Team
---

### Post by ejlal on 2010-01-12
salam 3alikom

i was browsing **[COLOR=Red][ubuntugeek.com]("http://www.ubuntugeek.com/")[/COLOR]**  when i came cross**[COLOR=Red][]("http://www.ubuntugeek.com/tipubuntu-sources-list-generator.html")[/COLOR]** an article about an easy way to generate a sources list.

i tried it and the final list looked very clean and tidy but i didn't add it to my /etc/apt/sources.list (too lazy to do it today)
[B]
so check it out[/B]:popcorn:          **[COLOR=Red][The Article]("http://www.ubuntugeek.com/tipubuntu-sources-list-generator.html")[/COLOR]**

**[COLOR=Red]if you plan to add it to your system dont forget to make a backup copy of your sources.list just in case things went bad...[COLOR=Black]*it's better to be safe than sorry,right?*[/COLOR][/COLOR]**

---

### Post by zero-n on 2010-01-12
---------------------------
      Before testing
---------------------------
[COLOR=Red][B]
if your want to test this web tool do it at your own risk[/B][/COLOR].

This is a command to backup your sources.list file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bakup
```so **sources.list.bakup** will be a backup file for **sources.list**






---------------------------
      After testing
---------------------------

it have a lot of 3rd party repositories but,

Where is [COLOR=Red]**Sudan**[/COLOR] in countries list ? :-s

and it didn't give me instruction about how to add the GPG key.


thanks it's a good way to restore at least the main repositories.

---

### Post by ejlal on 2010-01-12
> **zero-n said:**
> 


and it didn't give me instruction about how to add the GPG key.
am not sure but i think, you add it through the command line in the terminal.

---

### Post by zero-n on 2010-01-12
as i know you can the GPG form terminal or software sources.

but the web tool didn't give information about how to add this key.

alot of Ubuntu users are newbie so they need a more detailed instruction to help them.

this tool is good but not perfect

---

### Post by ejlal on 2010-01-12
> alot of Ubuntu users are newbie so they need a more detailed instruction to help them.
you are absolutely right.

---

