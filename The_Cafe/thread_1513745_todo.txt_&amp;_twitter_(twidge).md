---
title: "todo.txt &amp; twitter (twidge)"
date: 2010-06-20
forum: The Cafe
---

### Post by jesus.mor on 2010-06-20
I am probably late to this but I recently found out about todo.txt a cool little terminal app to organize your todo list. It's a pretty sweet application but I felt like I couldn't add to it if I wasn't by a computer or had internet access. So since I am trying to learn shell scripting and am an avid twitter user I decided to make a script that would let me add to my todo list by tweeting.

You need to have twidge installed although I'm fairly certain you could do the same with curl just replace the twidge parts.

I made a separate twitter account to keep things neat.

Replace directmessage_account with the account you made.
Replace twitterusername with your own username.

```

#!/bin/bash
#Get Recent Direct Messages sent to directmessage_account
echo `twidge lsdmarchive -us` | grep directmessage_account >> /path/to/todo.txt
#Remove sender/recipiant information since I like to keep 
sed -i 's/<twitterusername> <directmessage_account> //g' /path/to/todo.txt
#Remove blanklines to keep todo.txt formated right
sed -i '/^$/d' /path/to/todo.txt
#Search for keyword "dnes" and if it is there send a direct message to myself with the things that are due the next day and if not say "Not Found"
if grep -q "dnes" "/path/to/todo.txt" ; then
    grep `date --date '1 day' '+%m%d%y'` "/path/to/todo.txt" | sed 's/ /_/g' | xargs twidge dmsend twitterusername && sed -i 's/dnes//g' /path/to/todo.txt
else
    echo "Not found"
fi

```

I don't know if it will be useful to anyone but I thought I would share it.

Comments on how to clean up the code or what I can do to improve would be appreciated.

---

### Post by rubo77 on 2010-09-04
so can you do this with curl too?

---

