---
title: "Presenting world's smallest Twitter client [kindly improvise]"
date: 2010-08-22
forum: The Cafe
---

### Post by amitabhishek on 2010-08-22
[PHP]##Created/customised by: Amit Abhishek##
##Twitter ID: @amitabhishek##

echo 'enter Twitter ID (email)'
read name
echo 'enter password'
read password
echo 'enter message (140 chars)'
read message

wget --keep-session-cookies --http-user=$name --http-password=$password \
    --post-data="status= $message" \
    http://twitter.com:80/statuses/update.xml

rm -f update.xml.*[/PHP]

Created this lame as$ script to kill time (actually I am compiling Android source and it will take several hours on my rickety eeePC). Improvise the script if you can or just use it for fun :D.

some ideas:

-restrict input to 140 chars
-mask the password field

---

