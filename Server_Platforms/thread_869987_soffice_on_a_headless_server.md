---
title: "soffice on a headless server"
date: 2008-07-25
forum: Server Platforms
---

### Post by matthewboh on 2008-07-25
I finally got soffice working with KnowledgeTree by using the following command
```
soffice "-accept=socket,host=localhost,port=8100;urp;StarOffice.ServiceManager" -nologo -headless
```
I now have two questions - 

I've read several places the soffice has to be running as the same user as the web server.  However, it's currently running as me and knowledgeTree is running as www-data and it seems fine.  Do I need to change that?

Secondly, how / what's the best way to have soffice start up on boot?

Thanks all!

---

