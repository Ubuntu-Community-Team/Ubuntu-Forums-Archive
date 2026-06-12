---
title: "my first bash script"
date: 2008-10-29
forum: The Cafe
---

### Post by lennartack on 2008-10-29
Hi!

How do you like it? It's called ****. I was a little bored today ;).

```
#!/bin/bash

if [ "$UID" -ne "0" ]
then
  echo "Only root can ****"
  exit 67
fi

if [ -z "$1" ]
then
  echo "syntax: **** [victim]"
  exit 1
fi

if [ "$1" == "lennart" ]
then
  echo lennart cannot be ******
else
  echo "******* $1..."
  echo "You have been ******. To **** someone, run **** [victim]" | mailx -s "You have been ******" $1
  echo $1 has been ******
fi
```

---

