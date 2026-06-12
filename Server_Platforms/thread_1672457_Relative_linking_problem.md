---
title: "Relative linking problem"
date: 2011-01-20
forum: Server Platforms
---

### Post by tofuconfetti on 2011-01-20
I have hundreds of thousands of lines of PHP5 code invested in a long term project.  In trying to migrate the project I have an interesting problem.  Where links never required a ./ before items in the current directory, now they do.  I solved this one years ago, but for the life of me cannot find the solution.  I'm using Ubuntu 10.4 LTS recently installed with a downgraded version of PHP5 (5.2.10).  

Is this an Apache2 rewrite problem? 

As an example, this image link won't work:

```
<img src="images/button.png">
```

But this one will:

```
<img src="./images/button.png">
```

Any help would be appreciated.  Tnx.

---

### Post by wongo888 on 2011-01-20
Did you change directory levels?

ie. Before [http://www.example.com/index.php](http://www.example.com/index.php)

Now [http://www.example.com/myapp/index.php](http://www.example.com/myapp/index.php)

Or vice-versa?

What is the correct absolute path to the image?

---

