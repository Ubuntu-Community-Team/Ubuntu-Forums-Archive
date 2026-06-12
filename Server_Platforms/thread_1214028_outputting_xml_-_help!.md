---
title: "outputting xml - help!"
date: 2009-07-15
forum: Server Platforms
---

### Post by kapi on 2009-07-15
Hi there,

I apologize in advance for this question not being directly linked to Ubuntu but I am an ubuntu 9.04 user and everyone in the forums are so helpful, thanks for your patience.

I have had a request to output data as xml and am unsure as to how to go about it.

I have values taken from a html form on a web page that are sent to a php page. Then an SQL query searches a database (using php and mysql) using the form input as the SQL query parameters. From here I need to provide the results as XML.

I was thinking of writing the data to an xml document.

Can anyone help please

Thanks

---

### Post by t4thfavor on 2009-07-15
What language are you using, I think you could google (+write +xml +language) it.

---

### Post by BkkBonanza on 2009-07-15
Probably the simplest way is to use the SimpleXML functions in PHP. After you build a tree you can write it out as an xml document. See PHP docs. I've used these and they are quite easy to use.

---

### Post by kapi on 2009-07-15
Hi and thanks for the replies,

I had read about simple xml earlier. I think I'll give it ago

many thanks

Ubuntu rocks - and so do us that use it :-)

---

### Post by BkkBonanza on 2009-07-15
You should be able to use it to create a SimpleXML object and then add attributes and nodes etc. It behaves like an array but you need to figure out the details of how to manage the array because it is slightly unusual. Once you ahve the object as you like you can call the write function to put it in an xml file.

IIRC There are some examples in the function user notes that help.

---

