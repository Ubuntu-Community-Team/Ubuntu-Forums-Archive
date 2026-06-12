---
title: "do I really need virtual hosting if only hosting one site"
date: 2008-05-21
forum: Server Platforms
---

### Post by kustomjs on 2008-05-21
Hi Guys
I need to know if I really need virtual hosting for just hosting one site? if I do what would be the best away setting it up? if I don't what do I need to do to set it up?

---

### Post by kustomjs on 2008-05-21
wow this is pretty sad I got more replys within hour over on linuxquestions.org then here what is the problem here?

---

### Post by molotov00 on 2008-05-21
Poorly worded question. I'm glad you got your answer.

---

### Post by kustomjs on 2008-05-21
how can it be poorly worded question?

---

### Post by molotov00 on 2008-05-21
We don't know enough about what you require. Do you expect to add more sites in the future? Furthermore, if your question really is as simple as I think it is, a Google search will answer the question very quickly. Look up what the goal of a "virtual host" is. If you are talking about a virtual host in terms of Apache then that's something the Apache manual can tell you. 

Again, you haven't provided enough information for anyone to give you a meaningful response. And if all you are looking for is "a virtual host is not needed" then you could find that out very easily with a simple Google search.

---

### Post by kustomjs on 2008-05-21
my main question was do I have to have virtual host if only one site is hosted or not how simple can that get?

---

### Post by molotov00 on 2008-05-21
[http://httpd.apache.org/docs/1.3/vhosts/](http://httpd.apache.org/docs/1.3/vhosts/)

"The term Virtual Host refers to the practice of maintaining more than one server on one machine, as differentiated by their apparent hostname."

Read that as many times as you need. This is the very first sentence of the very first Google search result for 'Apache Virtual Host'.

According to the above definition, there is no virtual host if there is only one server on one machine. There is nothing virtual about that. I'm trying not to be a smart ***, but you are being ridiculously lazy, which is why I'm the only person to have responded.

---

### Post by kustomjs on 2008-05-21
you know I have been searching for hours and talked to alot of host masters and they told me to go to this forum to get help.

---

### Post by garethsimpsonuk on 2008-05-21
which is fine but people like you try at least 1 google search before you post, its common etiquette. in this case it would've found your answer. 

Also in your 2nd post saying stuff like 'wow this is pretty sad' isn't going to help you. Not even at linuxquestions.org

---

