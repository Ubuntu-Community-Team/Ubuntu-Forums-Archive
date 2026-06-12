---
title: "Remove those $$$$ dollar signs!"
date: 2008-06-01
forum: The Cafe
---

### Post by cardinals_fan on 2008-06-01
I modified the WebVocab user javascript to get rid of 'winblows', 'm$', and as many of those idiotic names as I could think of.  If anyone can think of some names I missed, mention them and I'll add 'em.  Here's the code:
```
// ==UserScript== 
// @name          WebVocab 
// @namespace     http://userscripts.org
// @description   Substitute second language vocab your studying into your primary language Web reading! //Modified version removing dumb names for Microsoft products
// @include       * 
// ==/UserScript== 


(function() {
  var replacements, regex, key, textnodes, node, s; 

textnodes = document.evaluate( "//body//text()", document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

for (var i = 0; i < textnodes.snapshotLength; i++) { 
    node = textnodes.snapshotItem(i); 

		if(node != null && node.nodeName == '#text' && /\S/.test(node.nodeValue))
		     {

    s = node.data; 
s = s.replace( /\bmicrosucks\b/gi, "Microsoft");
s = s.replace( /\bmicro\$oft\b/gi, "Microsoft");
s = s.replace( /\bmicrosoft\b/gi, "Microsoft");
s = s.replace( /\bms\b/gi, "Microsoft");
s = s.replace( /\bMs\b/gi, "Microsoft");
s = s.replace( /\bMS\b/gi, "Microsoft");
s = s.replace( /\bm\$\b/gi, "Microsoft");
s = s.replace( /\bM\$\b/gi, "Microsoft");
s = s.replace( /\bMicrosucks\b/gi, "Microsoft");
s = s.replace( /\bMicro\$oft\b/g, "Microsoft");
s = s.replace( /\bwindows\b/g, "Windows");
s = s.replace( /\bwindow\$\b/gi, "Windows");
s = s.replace( /\bwinblows\b/gi, "Windows");
s = s.replace( /\bwindblows\b/g, "Windows");
s = s.replace( /\bWindow\$\b/g, "Windows");
s = s.replace( /\bWinblows\b/g, "Windows");
s = s.replace( /\bWindblows\b/gi, "Windows");
s = s.replace( /\bWinsucks\b/g, "Windows");
s = s.replace( /\bvista\b/g, "Vista");
s = s.replace( /\bvi\$ta\b/g, "Vista");
s = s.replace( /\bVi\$ta\b/g, "Vista");
s = s.replace( /\bwindoze\b/g, "Windows");
s = s.replace( /\bWindoze\b/g, "Windows");


    node.data = s; 
		}
} 

})();
```

EDIT: Most of it works great, but the words 'm$' and 'M$' aren't replaced properly.  Can anyone see a problem?

---

### Post by bufsabre666 on 2008-06-01
all i can say is youre doing gods work, im so tired of all the bad names for ms and windows, people speak worse about microsoft than the genocide in darfur, its kinda sickening

---

### Post by -grubby on 2008-06-01
> **bufsabre666 said:**
> all i can say is youre doing gods work, im so tired of all the bad names for ms and windows, people speak worse about microsoft than the genocide in darfur, its kinda sickening

Yah, it's not like Microsoft is the bane of humanity or something. It really annoys me when people use things like "M$"

---

### Post by cardinals_fan on 2008-06-01
I'm kind of regretting the replacement, though.  Those names are always a great way to recognize a troll.

---

### Post by days_of_ruin on 2008-06-01
lol, of all the words to filter you chose...

---

### Post by Joeb454 on 2008-06-01
> **cardinals_fan said:**
> I'm kind of regretting the replacement, though.  Those names are always a great way to recognize a troll.

I won't use it then, that way somebody can recognise them ;)

---

### Post by cardinals_fan on 2008-06-01
> **days_of_ruin said:**
> lol, of all the words to filter you chose...
That's the point...

---

### Post by Kinst on 2008-06-01
How do you use it?

---

### Post by -grubby on 2008-06-01
> **Kinst said:**
> How do you use it?

If you're using Firefox, you can install greasemonkey and add it as a script, or something like that. I don't have greasemonkey, so I wouldn't know

---

### Post by monstermudder78 on 2008-06-01
Greatest waste of time.  Evah. 

Just my 2 cents.

---

### Post by SunnyRabbiera on 2008-06-01
you forgot doze :P

---

### Post by macogw on 2008-06-01
Why replace "MS"?  That's a normal way of abbreviating Microsoft.  That's like saying we must all say "Richard Matthew Stallman" not "RMS".

---

### Post by SunnyRabbiera on 2008-06-01
> **macogw said:**
> Why replace "MS"?  That's a normal way of abbreviating Microsoft.  That's like saying we must all say "Richard Matthew Stallman" not "RMS".

Indeed, what do we have to use thier stock name MSFT now???

---

### Post by Methuselah on 2008-06-01
LOL, I don't have a problem with any microsoft bashing anywhere.
However, the last place it would bother me is on a linux message board.

---

### Post by cardinals_fan on 2008-06-01
> **macogw said:**
> Why replace "MS"?  That's a normal way of abbreviating Microsoft.  That's like saying we must all say "Richard Matthew Stallman" not "RMS".
I'm a correctness freak.  Microsoft is more exact than MS.

---

