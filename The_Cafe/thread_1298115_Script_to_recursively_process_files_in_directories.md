---
title: "Script to recursively process files in directories and subdirectories?"
date: 2009-10-22
forum: The Cafe
---

### Post by potatan on 2009-10-22
Hi,

I have a load of PDF docs that I want to convert to .txt files so that I can use them as input for a bit of concordance software that I'm playing with.  The files are all in a big directory with subdirectories, so I need a way of running```
pdftotext
``` against all the files in all the directories, rather than converting them one at a time.

I'm thinking perhaps a bash script would do it, or even some kind of piped output from a "dir" command.

Any ideas, or anything prior that I can adapt?

Many thanks.

---

### Post by Tibuda on 2009-10-22
```
for f in * **/*; do
  pdftotext $f
done
```

---

### Post by diesch on 2009-10-22
```
find . -name \*.pdf -exec pdftotext "{}" \;
```

---

### Post by lswb on 2009-10-22
The find command will recurse through subdirectories and can execute a program on matches. For your needs, the command line would be

```

find /path/to/directory -exec pdftotext '{}' \;

```

If you only want to attempt converting files with an extension of ".pdf" 
```

find /path/to/directory -name "*.pdf" -exec pdftotext '{}' \;

```

---

### Post by potatan on 2009-10-22
Fantastic - thanks folks!

---

