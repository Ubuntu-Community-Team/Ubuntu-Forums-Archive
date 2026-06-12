---
title: "Apache and Symlink issues"
date: 2006-02-11
forum: Server Platforms
---

### Post by jlarkin on 2006-02-11
I have trying to get a symlink working under apache for a while now with no success. All I need is to enable directory browsing in a symlink that I have created inside the document root. I am a bit new to Ubuntu, but I have done everything that I have found on forums. Currently I have access for all of the files/dirs that I am linking to set as 774 (though I get the same results with 777). I have also added the www-data user to the group that owns all of the files. I have FollowSymLinks set in all places that seem to make sense. One thing that stands out to me is that ls -l shows the symlink as red. I really have not idea what the colors mean, but red doesn't seem good :).

---

### Post by heimo on 2006-02-11
It's a symlink to directory? Try removing it and creating it again and be sure to use correct path - it's probably just pointing to non-existent directory - that's why it shows as red in colored ls output.
```

ln -s /path/to/the/directory /path/to/symlink
```

---

### Post by jlarkin on 2006-02-11
I have done that now, but I pretty sure that the symlink (and yes, to a directory) is correct because I can list the files inside the link path and I get the contents that I expect. The directory that I am linking to is on another physical hard drive. I don't know if that might be a problem.

---

### Post by heimo on 2006-02-11
What's the response from web server if you enter the path (to the symlinked folder) in browser? 404? 403? Is it otherwise working as expected? (other files than the ones in symlinked directory) Run
```
tail -f /var/log/apache2/access.log
``` and
```
tail -f /var/log/apache2/error.log
``` while trying to access the files. Any hints there?
EDIT: Those paths to log files may vary (check from apache config files)

---

### Post by jlarkin on 2006-02-11
Ahh, I seem to have forgotten some of the details on my original post :). I am getting a 403 error when I try to view the symlinked folder. The log pretty much reflects the same thing.

---

### Post by breezyfox on 2006-02-11
[QUOTE=heimo]It's a symlink to directory? Try removing it and creating it again and be sure to use correct path - it's probably just pointing to non-existent directory - that's why it shows as red in colored ls output.
```

ln -s /path/to/the/directory /path/to/symlink
```[/QUOTE]

Hi ,I think the link code should be 
ln -s /path/to /directory <any name given to link>
It works in my case vwey well.

bz

---

