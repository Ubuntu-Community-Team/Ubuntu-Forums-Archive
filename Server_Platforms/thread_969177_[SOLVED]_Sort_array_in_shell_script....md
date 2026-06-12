---
title: "[SOLVED] Sort array in shell script..."
date: 2008-11-03
forum: Server Platforms
---

### Post by ragtag on 2008-11-03
How do I make all entries in an array unique. I've been trying something like:

```

my_array=( a b a a c)
unique_array=$(echo $my_array | sort -u)
for a in ${unique_array[@]}; do
    echo $a
done

```

What I'm hopint to get out is:
```

a
b
c

```

But what I get is just 'a'.

How would I go about this?

---

### Post by CrucifiedEgo on 2008-11-03
I think there's 2 things going on.  First, when i just do:
```
my_array=(a b a a c)
echo $my_array
```

i get "a".  You'll want to start out with a space-seperated string.  Second, i don't think sort will take space-seperated lists, they need to be seperated by new lines.  Here's what i ended up with that does exactly what you're looking for:

```

#!/bin/bash
my_array="a b a a c"
unique_array=$(echo $my_array | sed 's/ /\n/g' | sort -u)
for a in $unique_array; do
    echo $a
done

```

Hope this helps.

---

