---
title: "how to know the file which the process is working on"
date: 2011-03-30
forum: Server Platforms
---

### Post by that_is_lg on 2011-03-30
Hi all, 

I have a server. I installed apache on it. But my apache is working 99% and  i dont know why. 
I saw some process is working with Apache. I want to know what the file is working with these processes. 

Who can help me??

Im sorry because my E is not good

---

### Post by BkkBonanza on 2011-03-30
You might try seeing what info you can get from **lsof**. Use the -p option to specify the process id for the problem program and see what you can get from that.

See **man lsof** for ways to control what it shows you.

---

### Post by that_is_lg on 2011-03-31
> **BkkBonanza said:**
> You might try seeing what info you can get from **lsof**. Use the -p option to specify the process id for the problem program and see what you can get from that.

See **man lsof** for ways to control what it shows you.

thanks for your help. 
I did it. but how can i sort my result.

---

### Post by BkkBonanza on 2011-03-31
You can select only certain lines using grep and sort them by piping to sort. Also useful is awk. If you post a sample of what you have, and what you want, I may be able to suggest commands to get what you want.

---

