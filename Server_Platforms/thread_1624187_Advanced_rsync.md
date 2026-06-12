---
title: "Advanced rsync"
date: 2010-11-17
forum: Server Platforms
---

### Post by computerx138 on 2010-11-17
Thought I'd post it here because it's more server related than desktop...

I have a script that does:

```
rsync -Lrv --delete --exclude '.*' -e 'ssh -p xxx' xxx/  root@xxx.co.uk:/home/xxx/xxx/
rsync -Lrv --delete --exclude '.*' -e 'ssh -p xxx' xxx/ root@xxx.co.uk:/home/xxx/xxx/
rsync -lrv --delete --exclude '.*' -e 'ssh -p xxx' public_html/ root@xxx.co.uk:/home/xxx/public_html/
scp -P xxx public_html/.htaccess root@xxx.co.uk:/home/xxx/public_html/
ssh -p xxx root@xxx.co.uk 'chown -R xxx:xxx /home/xxx/public_html/*'
mysqldump --user=xxx --password=xxx xxx | ssh -p xxx root@xxx.co.uk "mysql --user=xxx --password=xxx xxx"

```

This is used to sync my local development snapshot with the live web server.

There has to be a more compact way of doing this? Can I combine some of the rsyncs? Can I make the rsync set or keep the user and group affiliations? Can I exclude .* yet include .htaccess?

---

### Post by koenn on 2010-11-17
the first 2 rsync lines look identical, you can remove one (unless I'm overlooking something)

rsync can preserve ownership and permissions (man rsync for  options), so the chown statement can go.

I think rsync also handles hidden (.*) files, so rsyncing public_html should already include .htaccess; but you might want to check this or see if you need to add a specific option to make it so.

---

### Post by computerx138 on 2010-11-17
> **koenn said:**
> the first 2 rsync lines look identical, you can remove one (unless I'm overlooking something)

rsync can preserve ownership and permissions (man rsync for  options), so the chown statement can go.

I think rsync also handles hidden (.*) files, so rsyncing public_html should already include .htaccess; but you might want to check this or see if you need to add a specific option to make it so.

This is where it gets more interesting.

The first two lines aren't identical in my script - I just obfuscated them for this example.

chown: The script transfers new files as well as updating existing files. The source files have a completely different user/group than they get chown'd to, so copying owner/group wouldn't work. It'd have to assign a specific user/group. I don't see an option for this.

I'm not sure it handles hidden files automatically, or even if included, but I could be wrong. Regardless, I only want it to copy .htaccess files, not any other hidden files.

I should also add: I'm not willing to enable shell access for the users the files are chown'd to.

---

### Post by koenn on 2010-11-17
ah, you left out all the relevant stuff. 

anyway, if the case is as you describe now, I'd leave it alone. 
You might be able to do something creative with the rsync src and dst paths to make the script a little more concise, but it's not worth the trouble (it won't run faster, you still have to compare each src with the corresponding dst and push the data over the wire) and might get more error prone or less human-readable.

So, if it gives you the result you want, leave it alone.

---

### Post by computerx138 on 2010-11-17
You're probably right ;)

I keep trying to push what I know to improve my shell knowledge. I love bash, I just wish I knew it better.

---

### Post by koenn on 2010-11-17
if you keep looking for things to automate, there'll be more and better opportunities to improve you bash skills and write beautiful scripts
:)

if you're pretty sure you'll always be using the same options to rsync, or find other common stuff (like the ssh port ?), you might want to try variables to hold them, so you only need to update them in 1 place in stead of in each statement, should the need ever arise.

eg something like (untested)```

OPT_RSYNC="-Lrv --delete --exclude '.*' -e 'ssh -p xxx'"
DST_SRV="root@xxx.co.uk"

rsync $OPT_RSYNC  xxx/        $DST_SRV:/home/xxx/xxx/
rsync $OPT_RSYNC xxx/         $DST_SRV:/home/xxx/xxx/
rsync $OPT_RSYNC public_html/ $DST_SRV:/home/xxx/public_html/

scp -P xxx public_html/.htaccess $DST_SRV:/home/xxx/public_html/

ssh -p xxx $DST_SRV 'chown -R xxx:xxx /home/xxx/public_html/*'


```
problem with this is, you sometimes need to be very careful with  " and '

---

### Post by Grant Walters on 2010-11-17
you could try using --filter=<file> to be more precise about the files included.  The - excludes files/dirs and the + includes them.  check the filter section of the rsync man page as matching occurs along the whole path unless you use full regexes, but it can be a good way to stop all of the development files created by frontpage and other tools from getting to your final destination.  The filter is applied when rsync selects files to copy so it is fast.

#
# Rsync Include/Exclude Filter For Web
#
+ .htpasswd
- somedir/
+ *\.[c|j|g|p][s|p|i|h][s|i|f|p]  <---- short for .css .jpg .gif .php
+ *\.html

Also, you can use the --numeric-ids flags if you are using the same uid and gid on the source as the destination but the names are different.

you are user(1000),group(1000) on source and web(1000),www-data(1000) on the destination.

I usually make the ids match on my local machine to facilitate this, allthough it may not be possible for you.

Hope this helps.

---

