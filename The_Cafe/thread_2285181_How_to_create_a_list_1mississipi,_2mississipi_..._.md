---
title: "How to create a list 1mississipi, 2mississipi ... all the way to 100mississipi?"
date: 2015-07-03
forum: The Cafe
---

### Post by bananaboatcoat on 2015-07-03
I want to create a list like this:

1mississipi
2mississipi
.
.
.
all the way to 
100mississipi


how can I create a regular text file containing all these, without having to type each manually?

---

### Post by angry_johnnie on 2015-07-03
This is one way to do it.

```
#!/bin/bash

for x in {1..100}
do
echo $x "mississipi"
done

```

btw to save to text you can pipe the output to a text file (./somescript.sh > file.txt)

---

### Post by bananaboatcoat on 2015-07-03
thank you, Angry Johnnie.

---

### Post by bananaboatcoat on 2015-07-03
How do I add the "pipe the output" part?

---

### Post by kostkon on 2015-07-03
> **bananaboatcoat said:**
> How do I add the "pipe the output" part?
Save the code as a text file, e.g. mississipi.sh, right-click on it, click Properties, then Permissions and make it executable.

Then cd in the folder and give:
```
./mississipi.sh > myoutput.txt
```

---

### Post by bananaboatcoat on 2015-07-03
thank you, kostkon.

---

