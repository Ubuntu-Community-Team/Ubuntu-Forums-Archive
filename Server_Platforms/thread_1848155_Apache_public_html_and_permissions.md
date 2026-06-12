---
title: "Apache public_html and permissions"
date: 2011-09-22
forum: Server Platforms
---

### Post by fernandoch on 2011-09-22
Hello,

Who should own the public_html? www-data or root?

And then what permissions would you give to the files in public_html?

Thank you.

---

### Post by Ryan Dwyer on 2011-09-22
It doesn't matter. The Apache user (usually www-data) only needs to be able to read the files. So if "other" has read access then it should work.

---

### Post by fernandoch on 2011-09-22
Thank you.

But what would be the "best practice"?

---

### Post by Ryan Dwyer on 2011-09-22
It depends on your setup. If the server administrators manage the website directly then it may as well be owned by root with www-data having readonly access via other. If you need to be able to edit the website as a non-root user (eg. via FTP) then the files should be owned by that user, again with www-data having readonly access via other.

---

### Post by fernandoch on 2011-09-22
OK, thank you guys.

---

### Post by Lars Noodén on 2011-09-22
www-data should **not** own public_html.  If it does then the web server can re-write it.  www-data is the group used by the web server and is the default groups for any processes or scripts that it calls. Bugs, errors, misconfigurations and misfeatures in a script would also have those write permissions. So giving write access to web directories to the user or group www-data could allow uninvited guests to make use of your system in ways that you might not find the most enjoyable.

What you can do is make another group, say 'webmasters' and then make the directory a member of that group and make any users who should have write access also members.  Or just leave it as root.

---

### Post by Wim Sturkenboom on 2011-09-22
One of the scenarios where apache needs write permissions is if you have an upload functionality on your site, e.g. a photo website where visitors can upload photos.

How would apache do that without write permissions?

---

### Post by Lars Noodén on 2011-09-22
In that case you would need a separate directory and have nothing else there at all.  Giving carte blanch to the server to write is almost asking for something unpleasant to happen.

---

### Post by Dangertux on 2011-09-22
> **Lars Noodén said:**
> In that case you would need a separate directory and have nothing else there at all.  Giving carte blanch to the server to write is almost asking for something unpleasant to happen.

+1

Keep it owned by root or a different group all together. 

In cases like wordpress where you have your "uploads" directory, you will notice it is separate and you can change your permissions / ownership of that directory based on the need to upload. 

The concept is it is protected by the permissions of its parent directory, even then this is not the greatest idea.

---

### Post by fernandoch on 2011-09-22
Well for wordpress it is owned by www-data according to this

[https://help.ubuntu.com/community/WordPress#Install_Wordpress](https://help.ubuntu.com/community/WordPress#Install_Wordpress)

---

