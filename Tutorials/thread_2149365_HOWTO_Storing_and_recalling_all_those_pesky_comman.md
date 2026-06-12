---
title: "HOWTO: Storing and recalling all those pesky command line commands and code snippets"
date: 2013-05-28
forum: Tutorials
---

### Post by mikeym on 2013-05-28
Hi,

I've put up [a post on my blog]("http://www.green-spot.co.uk/2013/05/21/storing-and-searching-code-snippets-with-metadata/") with a perl script that I've found very useful in leaning commands and how to use the command line. 

I found with using the command line I was prone to forgetting commands or snippets of code that I used irregularly. So I made [this Perl script]("http://www.green-spot.co.uk/blog/public/cl") which helps store code snippets along with some meta information to be able to search and retrieve them later. 

[IMG]http://www.green-spot.co.uk/blog/wp-content/uploads/2013/05/CommandList-scalled2.png[/IMG]

It displays the code snippet with syntax highlighting so that you can see what it does before running it, which I have found helps me learn the command or code. 

You can install it by putting it into your path, I'd recommend somewhere owned by root such as /usr/locla/bin/ and making it executable with:

```

chmod +x /usr/local/bin/cl

```

The dependencies can be installed with:

```

sudo apt-get install perl libxml-twig-perl libsyntax-highlight-engine-kate-perl

```

Maybe it will be of some help to someone. :)

---

