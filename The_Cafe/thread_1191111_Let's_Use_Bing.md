---
title: "Let's Use Bing"
date: 2009-06-18
forum: The Cafe
---

### Post by Dragonbite on 2009-06-18
I think all Linux users should use [[COLOR="Blue"]Bing [/COLOR]]("http://www.bing.com/")to search for Linux-related things.  So when Microsoft goes to see what the top searches are, let them see "Linux" or "Ubuntu" or "Red Hat" or "MySQL" or anything else FOSS related!

---

### Post by brian183 on 2009-06-18
I dunno, kinda cool idea but they don't deserve our traffic.

---

### Post by jamieh on 2009-06-18
Try searching for "WHY DOES WINDOWS SUCK SO MUCH?!" or something, lol.

---

### Post by sim-value on 2009-06-18
Stupid idea in my Opinion because all they get from it is Marketshare ....

---

### Post by Tibuda on 2009-06-18
This script can help, but it will waste your connection if you keep it running:
```
#!/bin/bash

if [ -n "$*" ]; then
  WORDS="$*"
else
  WORDS="linux apache php mysql mozilla firefox openoffice gimp ubuntu fedora mandriva redhat foss opensource gnu ogg jabber xmpp"
fi

while true; do
  for WORD in $WORDS; do
    echo "Searching BING for $WORD"
    wget http://www.bing.com/search?q=$WORD --header='Accept-Language: en' \
      -o /dev/null -O - | grep "[0-9,]\+ results" -o
    sleep 1
  done
  echo
done
```

---

### Post by forrestcupp on 2009-06-18
> **Dragonbite said:**
> I think all Linux users should use [[COLOR="Blue"]Bing [/COLOR]]("http://www.bing.com/")to search for Linux-related things.  So when Microsoft goes to see what the top searches are, let them see "Linux" or "Ubuntu" or "Red Hat" or "MySQL" or anything else FOSS related!

And they'll be crying all the way to the bank ...

They make money off of your searches.

---

