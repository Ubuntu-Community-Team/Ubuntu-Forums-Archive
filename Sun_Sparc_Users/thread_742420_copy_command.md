---
title: "copy command"
date: 2008-04-01
forum: Sun Sparc Users
---

### Post by tfrancis6666 on 2008-04-01
I am looking for a command to copy all files from one directory to another except for certain files or a directory from the original location. Without having to copy each and every file Individually. Can anyone help me

---

### Post by marpstar on 2008-04-01
cp is a pretty powerful copy utility that's available within the terminal

[http://unixhelp.ed.ac.uk/CGI/man-cgi?cp](http://unixhelp.ed.ac.uk/CGI/man-cgi?cp)


read that, it's very powerful and can easily do what you've just said.

---

### Post by ghostdog74 on 2008-04-02
```

for files in *
do
  case $files in
   *.txt ) echo "this is not needed to cp; continue ;;
   * ) cp "$files" "$destination" ;;
  esac
done 

```

---

