---
title: "Different colored terminals on each machine"
date: 2011-10-23
forum: The Cafe
---

### Post by hwttdz on 2011-10-23
My weekend project has been combining my .bashrc's on all the machines I work on (because I get confused easily).  And I like to have different prompt colors on each machine to tell me what machine I'm on.  Anyways I simplified the prompt stuff into using an md5 hash of the hostname.  Which is nice, because it assigns each machine a color.  I've reserved 31 (red) for root (having a big red prompt telling you you're root is nice in my mind).  I've also mapped the colors a little differently. They're more or less every 40 hue degrees, starting at 0 (red) and skipping 120 (green, my terminal text is green).  This gives me a bunch of usable colors that I can differentiate between easily (for things like ls).  

I don't to a hex to decimal conversion because 1) I was having issues with the piping to bc and whatnot, and 2 because this gives me all I need.

```
HOSTHASH=`hostname --fqdn| md5sum -|awk '{print $1}'`
HOSTHASH=`echo $HOSTHASH|tr -d '[a-f]'` # removes all letters
let HOSTHASH=$HOSTHASH%100000000
export HOSTHASH

let COLORCODE=$HOSTHASH%7+30
if (( $COLORCODE > 30 )); then
	let COLORCODE=$COLORCODE+1
	export COLORCODE
fi

PS1='\n\[\033[1;${COLORCODE}m\]\u `date +%T --date="now - $OFFSET seconds"` @ \h \w>\[\033[0m\] ' # set the prompt
```

---

### Post by Gremlinzzz on 2011-10-23
Yeah i mess with every thing startup sound,my terminal green/black background,use to mess with start splash but no so much any more.
that i use to do with windows to.:popcorn:

---

