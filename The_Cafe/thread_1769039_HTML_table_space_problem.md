---
title: "HTML table space problem"
date: 2011-05-27
forum: The Cafe
---

### Post by rmcellig on 2011-05-27
I am hoping that there is a HTML table expert in this forum. For some reason, there is a lot of space before my actual table and I don't know what is causing this and how to fix it. I've attached a copy of the HTML file.

---

### Post by lucazade on 2011-05-27
> **rmcellig said:**
> I am hoping that there is a HTML table expert in this forum. For some reason, there is a lot of space before my actual table and I don't know what is causing this and how to fix it. I've attached a copy of the HTML file.

remove all the <br/> tags from your page.. are not necessary and take all the space at the top!

---

### Post by rmcellig on 2011-05-27
Thank you so much lucazade for your super fast response!!!! I really appreciate this!!!! Do you think that using tables is the best way for me to display this data or is there a better way that I am not aware of?

---

### Post by lucazade on 2011-05-27
I believe for simple purposes are html tables are enough.. you could add a bit of style and color to them using CSS

take a look a this page:
[http://www.w3schools.com/css/css_table.asp](http://www.w3schools.com/css/css_table.asp)

here you can try and modify the example live:
[http://www.w3schools.com/css/tryit.asp?filename=trycss_table_fancy](http://www.w3schools.com/css/tryit.asp?filename=trycss_table_fancy)

---

### Post by rmcellig on 2011-05-27
Thanks again! I was thinking of doing some CSS styling after I make sure that all of my data is in my table.

---

### Post by lucazade on 2011-05-27
You are welcome!

If you are looking for something better, and you want to spend a little time implementing it, I could suggest to use ExtJS framework 
[http://www.sencha.com/products/extjs/examples/](http://www.sencha.com/products/extjs/examples/)

take a look at this cool table ;)
[http://dev.sencha.com/deploy/ext-4.0.1/examples/grid/array-grid.html](http://dev.sencha.com/deploy/ext-4.0.1/examples/grid/array-grid.html)

---

### Post by rmcellig on 2011-05-27
I will definitely take a look. By the way, where exactly does the CSS code go in my HTML document. Thanks!

---

### Post by lucazade on 2011-05-27
> **rmcellig said:**
> I will definitely take a look. By the way, where exactly does the CSS code go in my HTML document. Thanks!

at the top of your html document between the <style>...</style> tags

---

### Post by rmcellig on 2011-05-27
OK. Thanks.

---

### Post by Zero2Nine on 2011-05-27
Or you might keep it in an external file if you want to apply the style to more than one document. [http://www.w3schools.com/Css/css_howto.asp](http://www.w3schools.com/Css/css_howto.asp)

---

### Post by rmcellig on 2011-05-27
What distro are you using? I'm trying out Pinguy. I am looking for a distro that is easy to install and has everything included that Ubuntu lacks like some of the files you have to add after installing Ubuntu. Any suggestions for other user friendly distros that work well and require minimal updating (if possible :))

---

### Post by Bandit on 2011-05-27
> **rmcellig said:**
> Thank you so much lucazade for your super fast response!!!! I really appreciate this!!!! Do you think that using tables is the best way for me to display this data or is there a better way that I am not aware of?

Modern web designers are starting to steer away from the use of tables as much as possible, although they still have their place. Now webdesigners are using Divs <div> or organize data. 

Take a look at W3C Schools website for more information.

---

### Post by rmcellig on 2011-05-27
Thanks Bandit! Would you have an example or link to an example? I couldn't find one on the W3C Schools website.

---

### Post by jhonan on 2011-05-27
> **rmcellig said:**
> Thanks Bandit! Would you have an example or link to an example? I couldn't find one on the W3C Schools website.

[http://mindrulers.blogspot.com/2008/03/create-table-using-css.html](http://mindrulers.blogspot.com/2008/03/create-table-using-css.html)

---

### Post by Bandit on 2011-05-28
> **rmcellig said:**
> Thanks Bandit! Would you have an example or link to an example? I couldn't find one on the W3C Schools website.

Sure :-) [http://www.w3schools.com/tags/tag_DIV.asp](http://www.w3schools.com/tags/tag_DIV.asp)

---

### Post by Zero2Nine on 2011-05-28
> **Bandit said:**
> Modern web designers are starting to steer away from the use of tables as much as possible, although they still have their place. Now webdesigners are using Divs <div> or organize data. 

Take a look at W3C Schools website for more information.

Tables for layout are generally regarded as bad practice. But if you want to display tabular data... that's where the <table> element was designed for. Or maybe my html knowledge is outdated ;)

---

