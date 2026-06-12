---
title: "Writing Phrase from file based on number (bash)"
date: 2018-10-11
forum: Ubuntu Application Development
---

### Post by Lewis Arthurton on 2018-10-11
Hello Guys,

Sorry if this has been posted elsewhere I was just hoping you could help with me an problem I'm having with a bash script.

Essentially I have a file with:

XYZ (TAB) 45
CRW (TAB) 1
CLP (TAB) 5

I want the script to write to another file XYZ because the number after the tab is over 30. The others the script should be ignore because they are below 30.

How would I go about doing this? I'm struggling a bit with the syntax for it and was hoping to learn from the example. Sorry I realise this is a big ask.

Thanks

Lewis

---

### Post by &amp;KyT$0P# on 2018-10-11
I would split the file contents into two arrays, then iterate through the array indices -
```
#!/bin/bash

# This is the path to the file containing that data
yourfile='./test.txt'

# Parse the file into two arrays, one of the names (e.g. XYZ) and another of the numbers
names=($(cat "$yourfile" | sed -r -e 's/\t.*$//g'))
numbers=($(cat "$yourfile" | sed -r -e 's/^.*\t//g'))

# Process the arrays by iterating through the indices
# Note: this assumes the two arrays are the same length
for i in $(seq 0 $((${#names[@]} - 1)));do
  if [[ "${numbers[$i]}" -gt 30 ]];then
    # do what you want with "${names[$i]}" here
  fi
done

```

---

### Post by Lewis Arthurton on 2018-10-12
Hello halogen2

Many thanks for the quick reply I should have been more specific with my request my apologies, 

My file is actually more similar to:
Here Is Some Text     30
Hello World               10
More Text                 1

I've edited the code you wrote adding in:

```
# Parse the file into two arrays, one of the names (e.g. XYZ) and another of the $
names=($(cat "$yourfile" | sed -r -e 's/\t.*$//g'))
numbers=($(cat "$yourfile" | sed -r -e 's/^.*\t//g'))

# Process the arrays by iterating through the indices
# Note: this assumes the two arrays are the same length
for i in $(seq 0 $((${#names[@]} - 1)));do
  if [[ "${numbers[$i]}" -gt 30 ]];then
    # do what you want with "${names[$i]}" here
**echo "${names[$i]}" >> 2.tmp**
```

However the code writes to file like this: 

```
Here
is 
some
text
hello
world
more text
```

How would I edit the command to write to file: 

```
Here Is Some Text    
Hello World              
More Text  
```

Many thanks once again for all your help 

Lewis

---

### Post by steeldriver on 2018-10-12
If you have a column of space-separated text followed by a tab-delimited number, then the obvious way to process it would be using awk e.g.

```

awk -F '\t' '$2+0 > 30 {print $1}' file.txt

```

---

