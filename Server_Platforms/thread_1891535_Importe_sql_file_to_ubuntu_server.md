---
title: "Importe sql file to ubuntu server"
date: 2011-12-05
forum: Server Platforms
---

### Post by barezi6 on 2011-12-05
hi everyone, i am making this new thread because my other thread about this problem, isnt the best because have some other problems that was resolved and is a little confused about this problem. When i was building my website i use a localhost (xampp) to create my database, and now i have a dedicated server, with ubuntu, and now i exporte my database created on localhost (xampp) to a sql.file that was saved on my local computer, now i have the local computer that have the sql file and a server computer with ubuntu, and now i need to import this file from my local computer to the server computer, i searched some about it, but dont see anything that could help, anyone can give me some help? 
Thanks

---

### Post by maverickaddicted on 2011-12-06
1) If you have a phpmyadmin access, you can directly upload it by logging to phpmyadmin page of your server.

2) If you do not have phpmyadmin access, then you can upload it via SSH login to your server -

      a) upload the sql file in your server.
     
      b) run this command
          
          ```
mysql -p -u username database_name < file.sql
```

---

### Post by barezi6 on 2011-12-06
> **maverickaddicted said:**
> 1) If you have a phpmyadmin access, you can directly upload it by logging to phpmyadmin page of your server.

2) If you do not have phpmyadmin access, then you can upload it via SSH login to your server -

      a) upload the sql file in your server.
     
      b) run this command
          
          ```
mysql -p -u username database_name < file.sql
```

problem resolved 

Thanks very much :)

---

### Post by maverickaddicted on 2011-12-06
You are welcome. If the problem is resolved, do not forget to mark the thread as closed.

---

