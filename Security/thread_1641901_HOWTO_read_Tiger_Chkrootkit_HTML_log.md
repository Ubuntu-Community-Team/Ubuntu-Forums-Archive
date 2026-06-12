---
title: "HOWTO read Tiger Chkrootkit HTML log?"
date: 2010-12-09
forum: Security
---

### Post by bachor on 2010-12-09
sudo tiger -H   

 logged to:   /var/log/tiger    in .HTML format

 how do I read it?

 Nautilus ->  no permission!

 is there a command for it?

---

### Post by BbUiDgZ on 2010-12-09
> **bachor said:**
> sudo tiger -H   

 logged to:   /var/log/tiger    in .HTML format

 how do I read it?

 Nautilus ->  no permission!

 is there a command for it?

```
sudo firefox /path/to/html/file
```

---

### Post by OpSecShellshock on 2010-12-09
You can also drag the file over a firefox window and just drop it in.

---

### Post by bodhi.zazen on 2010-12-09
Usually the output is owned by root and only root can read it. It has a long file name with date/time stamp, so use tab completion

```
# copy the fiel to home
sudo cp /var/log/tiger/outfile ~your_login_name #it has a long name, use tab completion

#change ownership
sudo chown your_login_name:your_login_name ~/outputfile

#open w/ firefox
firefox ~/outputfile
```

---

### Post by OpSecShellshock on 2010-12-10
> **bodhi.zazen said:**
> Usually the output is owned by root and only root can read it. It has a long file name with date/time stamp, so use tab completion

```
# copy the fiel to home
sudo cp /var/log/tiger/outfile ~your_login_name #it has a long name, use tab completion

#change ownership
sudo chown your_login_name:your_login_name ~/outputfile

#open w/ firefox
firefox ~/outputfile
```

This is a good point, and the ownership change is a very important step.

---

### Post by bachor on 2010-12-10
> **BbUiDgZ said:**
> ```
sudo firefox /path/to/html/file
```

it won't let me,see bellow

> **OpSecShellshock said:**
> You can also drag the file over a firefox window and just drop it in.

can't do that,folder is locked,see bellow

> **bodhi.zazen said:**
> Usually the output is owned by root and only root can read it. It has a long file name with date/time stamp, so use tab completion

```
# copy the fiel to home
sudo cp /var/log/tiger/outfile ~your_login_name #it has a long name, use tab completion

#change ownership
sudo chown your_login_name:your_login_name ~/outputfile

#open w/ firefox
firefox ~/outputfile
```


bodhi,you are right,it needs root,but when I try to open it got this:

root@pawel-Inspiron-6000:/var/log/tiger# firefox security.report.pawel-Inspiron-6000.101209-14:00.html
No protocol specified
No protocol specified
Error: cannot open display: :0.0

and only Apparmor [with your firefox profile ;) ]  window pops up.

Could you please help me what means this tab completion? : 

#it has a long name, use tab completion

thank you all :D

---

### Post by bachor on 2010-12-10
ok,got it:   1. cp to /home     2. sudo chown root:     3. chmod g+r  for read permission  and it works   thank you and sorry for newbie questions

---

### Post by bodhi.zazen on 2010-12-10
Glad you got it sorted.

---

