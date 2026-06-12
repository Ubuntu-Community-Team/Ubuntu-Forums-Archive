---
title: "Need help to create a photo gallery"
date: 2011-06-26
forum: Server Platforms
---

### Post by coldraven on 2011-06-26
Some time ago I created a web-site for a local charity, it's a museum.
I wrote it all in HTML as that's all I knew. Now I need to archive lots of images and put them in a gallery. From a previous post I learned of Drupal, Joomla and Gallery.
The problem is I really don't know where to start. I've attached some details of the server.

My questions are -
Will my hosting company allow me to install a CMS like Drupal or do I have to use only the modules they supply?
How can I set up a test site alongside the existing one and merge them later? 
How should I arrange the directories for a gallery with, say, 10 categories?
How do I prevent any security weaknesses like SQL injection from happening?

That's enough questions for now, links to any tutorials for dummies would be appreciated.

---

### Post by SeijiSensei on 2011-06-26
> **coldraven said:**
> My questions are -
Will my hosting company allow me to install a CMS like Drupal or do I have to use only the modules they supply?

If they support PHP and MySQL or PostgreSQL, then you shouldn't have any problems with a CMS.  Of course, the only one who can answer this question is your hosting company.  Otherwise we'll all just be speculating here.

> How can I set up a test site alongside the existing one and merge them later?

Put it in a separate directory under the DocumentRoot.

> How should I arrange the directories for a gallery with, say, 10 categories?

What's wrong with 

/images/category1
/images/category2
...

as a structure?  What else would you choose?

> How do I prevent any security weaknesses like SQL injection from happening?

Read up on the security of the CMS you choose, I guess.  

You might want to do some additional searching at Google for alternatives to a CMS.  That's rather overkill for a photo gallery.  There are PHP-based gallery programs that don't require a database.

---

### Post by coldraven on 2011-06-26
> You might want to do some additional searching at Google for  alternatives to a CMS.  That's rather overkill for a photo gallery.   There are PHP-based gallery programs that don't require a database. 	

Thanks SeijiSensei, I will have to bite the bullet and learn PHP. I have a friend who knows it so I'll have to pick his brains. I'm good at copy and paste :)

---

### Post by arrrghhh on 2011-06-26
> **coldraven said:**
> Thanks SeijiSensei, I will have to bite the bullet and learn PHP. I have a friend who knows it so I'll have to pick his brains. I'm good at copy and paste :)

What about something like [gallery2](http://gallery2.org/)?

---

### Post by SeijiSensei on 2011-06-27
> **coldraven said:**
> Thanks SeijiSensei, I will have to bite the bullet and learn PHP. I have a friend who knows it so I'll have to pick his brains. I'm good at copy and paste :)

Most PHP applications are just drop-in items that you put somewhere in the web tree.  Complex applications like Drupal come with an installer. In neither case do you need to learn PHP, though it's certainly worth the effort if you think you'll be doing web development.

---

### Post by coldraven on 2011-06-28
Thanks everyone for your input.
I think that I will go with plain PHP and no MySQL. I have learned some more about my hosting company and the modules they support.
I downloaded the Jumpbox Joomla and ran it as a VM. It works well but is overkill for what I need. I will mark this thread solved.

---

