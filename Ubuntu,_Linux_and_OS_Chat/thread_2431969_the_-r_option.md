---
title: "the -r option"
date: 2019-11-25
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-11-25
the [COLOR=#0000cd][FONT=courier new]**touch**[/FONT][/COLOR] command has 2 options to reference another file object:  [COLOR=#800080][FONT=courier new]**--reference**[/FONT][/COLOR] and [COLOR=#800080][FONT=courier new]**-r**[/FONT][/COLOR]
the [COLOR=#0000cd][FONT=courier new]**chmod**[/FONT][/COLOR] and [COLOR=#0000cd][FONT=courier new]**chown**[/FONT][/COLOR] commands can reference another file object but they only have [COLOR=#800080][FONT=courier new]**--reference**[/FONT][/COLOR] to do that and not [COLOR=#800080][FONT=courier new]**-r**[/FONT][/COLOR]
anyone know why?  is there a security issue?

---

### Post by yetimon_64 on 2019-11-26
> **Skaperen said:**
> **[COLOR=#800080]...[/COLOR]**
the [COLOR=#0000cd][FONT=courier new]**chmod**[/FONT][/COLOR] and [COLOR=#0000cd][FONT=courier new]**chown**[/FONT][/COLOR] commands can reference another file object but they only have [COLOR=#800080][FONT=courier new]**--reference**[/FONT][/COLOR] to do that and not [COLOR=#800080][FONT=courier new]**-r**[/FONT][/COLOR]
anyone know why?  is there a security issue?

Most likely for safety reasons as chmod and chown both use "-R" for "recursive"; whereas touch has no recursive action option at all so it is safe to use "-r" for "reference".

If "-r" was used for "reference" with chown or chmod a simple accidental capitalization of "-r" to a "-R" could have a rather interesting/unexpected, possibly damaging, outcome. The recursive switch in some commands can at times have rather damaging consequences when used wrongly.

I have not read or heard of this as an explanation, I am only surmising this is the case. From my experience it is sort of obvious to me this would be why but I have not heard or seen elsewhere this situation explained, as a result you should await further advice from more experienced helpers here. There may be other explanations I am unaware of for this.

Regards, yeti.

---

### Post by Skaperen on 2019-11-26
that seems like a reasonable cause.

---

