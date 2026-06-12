---
title: "Can't install web-apps with Tomcat?"
date: 2006-07-14
forum: Server Platforms
---

### Post by NunoCorreia on 2006-07-14
Hi folks.

I installed the tomcat5 packages (as well as tomcat5-admin and tomcat5-webapps) from universe. I managed to get the server running and configuring the users.xml file I could use Tomcat Manager, but now I can't add my own pages.

Since I don't need to use servlets yet, I skipped the WEB-INF/web.xml part, and I simply tried symlinking to a directory that contained just an index.jsp file with some HTML in /usr/share/tomcat5/webapps. But then, accessing [http://localhost:8180/directory/](http://localhost:8180/directory/) gives me a 404. Appending index.jsp to the URL gave no luck either.

I don't quite want to use WARs yet because I'll be editing a lot right now.

What's wrong?

---

### Post by Gustavo Orair on 2006-09-26
Tomcat have a configuration about following symlinks!!!
Try Tomcat Documentation for this!!!

---

