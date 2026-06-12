---
title: "repair corrupted  win files"
date: 2010-01-05
forum: Wine
---

### Post by rjagathe on 2010-01-05
I use both winxp home and kubuntu(as Live CD)My computer is heavily corrupted.When I try to use Trial version of some AVs ,it deletes all my corrupted files.But, I have lot of data in my files I want to remove  virus and at the same time repair my corrupted files.Is there any SW for that? Can I use Ubuntu or some other Open source OS?

---

### Post by x33a on 2010-01-05
I don't think there is any such software that'll do this for you.

for program files, you'll simply have to reinstall the software, if the files are corrupt or deleted.

for other files, like doc, pdf, xls etc. see if they open up in openoffice, and if they do, try saving them as a different file.

also, you could give the strings command a try. it'll search a file for text, and extract the readable parts.

usage:
```
strings /path/to/file > output
```

in the above command, the extracted text will be redirected to a file named output, in the current directory.

---

