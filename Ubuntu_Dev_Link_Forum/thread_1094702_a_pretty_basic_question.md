---
title: "a pretty basic question"
date: 2009-03-12
forum: Ubuntu Dev Link Forum
---

### Post by Somiac on 2009-03-12
I couldn't find this, but lets say I have like 100 images on my desktop,
starting with SSL in it's name, most of them are like SSL262374.jpg and such.

If I want to use a command in the console, what would be best to move ALL of them to a different folder?

Now I don't want to say all files ending in .JPG because theres some other images from a different memory card that I want to keep there?

---

### Post by thesavager on 2009-03-12
You can do something like this:

```
mv SSL*.jpg /home/tmp
```

the above code , moves all files starting with SSL to the /home/tmp map, the joker * character, substitudes the numbers behind SSL, and they are jpg.

cheers..

---

