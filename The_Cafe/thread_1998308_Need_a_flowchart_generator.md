---
title: "Need a flowchart generator"
date: 2012-06-06
forum: The Cafe
---

### Post by stobbsm on 2012-06-06
Hi everyone,

I may be taking over development of a large website soon, but the first part of the project will be to fix the broken mess that currently exists.

I'm wondering if there are any tools that could help me automate the process of analying the website, and generate a decent flowchart.

I'll also need something to validate css and html from the command line, as well as verify all the URL's.

It is a huge site, and I would rather spend most of my time on development rather then seeing what's broken before I fix it.

Any suggestions? Any other information needed?

I'm looking for as little human interaction as possible, as I have a lot on the go, and I'm only one man.

---

### Post by Lars Noodén on 2012-06-06
For validating XHTML from the shell or via shell script, you can use [HTML Tidy](http://tidy.sourceforge.net/).  It's in the repositories.  I've used it in scripts before and it has a *lot* of options.  

For CSS validation, you might try the W3C's validator:
[http://jigsaw.w3.org/css-validator/DOWNLOAD.html](http://jigsaw.w3.org/css-validator/DOWNLOAD.html)

That would be my first guess.

---

### Post by CharlesA on 2012-06-06
> **Lars Noodén said:**
> For validating XHTML from the shell or via shell script, you can use [HTML Tidy](http://tidy.sourceforge.net/).  It's in the repositories.  I've used it in scripts before and it has a *lot* of options.  

For CSS validation, you might try the W3C's validator:
[http://jigsaw.w3.org/css-validator/DOWNLOAD.html](http://jigsaw.w3.org/css-validator/DOWNLOAD.html)

That would be my first guess.
Making sure the XHTML validates ok would be the first thing I do.

A few of the validation services tell you why it fails validation.

I use TotalValidator to verify my site is compliant.

---

### Post by stobbsm on 2012-06-06
I'll look at Tidy to validate the code, but I really need something to help generate the flowchart I need.

After looking at a few files, all of them prefixed index, ending with either .htm .html or .php, I've found there are 5 copies of the same thing, with slightly different names, but they all reference difference files.

ie. in index.html, there are references to videos.php, photos.htm and login.php.
in index.htm, there are references to videos.html, photos.php and login.html.

I need to sort out what is going where before I try to fix it all, to get the right path set.

It's a mess.

I'll report back about HTML Tidy. Thanks alot!

---

### Post by CharlesA on 2012-06-06
That sounds like a hell of a mess to fix. :(

Check out TotalValidator - it can verify links, xhtml and css all in one shot, however only if Pro version can be run on an entire site.

The free version can only be run a page at a time.

---

### Post by stobbsm on 2012-06-07
> **CharlesA said:**
> That sounds like a hell of a mess to fix. :(

Check out TotalValidator - it can verify links, xhtml and css all in one shot, however only if Pro version can be run on an entire site.

The free version can only be run a page at a time.

It is quite a mess. I created a small script to check all the htm, html and php files using tidy and it came up with 1463 errors! It seems the majority of them are unterminated tags (whoever did this before forgot to close a lot of divs).

EDIT: I'll look into TotalValidator. I'm downloading it now. We'll see what I can get from it.

---

### Post by CharlesA on 2012-06-07
> **stobbsm said:**
> EDIT: I'll look into TotalValidator. I'm downloading it now. We'll see what I can get from it.

It's written in Java, so you will need JRE installed to run it, but it should tell you what errors are there and how to fix them. :)

I prefer the Pro tool, but it also costs around $40 USD (or £25).

Good luck!

---

### Post by HermanAB on 2012-06-07
Doxygen?

---

### Post by lisati on 2012-06-07
> **HermanAB said:**
> Doxygen?

Interesting suggestion, which could be useful for more than debugging websites. I'm checking it out for one of my machines, it seems to want to download a lot of dependencies.

---

### Post by stobbsm on 2012-06-07
TotalValidator, while looking interesting, doesn't do what I need it to when I am still experimenting. Can't pay $40 when I'm not sure it will actually give me the reporting I want.

Using Tidy, I've at least got a good report coming along, and wrote a script to automate it.

[http://paste.ubuntu.com/1028159/]("http://paste.ubuntu.com/1028159/")

Feel free to use it, add to it, whatever.

I will be looking into doxygen as well for generating better reports, but initially, at least I now know what work I have ahead of me (yikes!)

FYI: Running my script in the root directory, just looking at HTML files (obviously), I'm getting 4148 errors. Next, I will have it generate some diffs for me, after having it make a "fixed" version.

---

### Post by Lars Noodén on 2012-06-07
For graphing you might look at Cytoscape or Graphviz

[http://www.cytoscape.org/](http://www.cytoscape.org/)
[http://www.graphviz.org/](http://www.graphviz.org/)

Both allow for network visualization, which sounds like what you are trying to with untangling your web site.

---

### Post by stobbsm on 2012-06-07
Looking into graphviz for mapping out the links.

I'll look to modifying the script I created earlier to include this if I get it working.

That reminds me, I have version 0.2 of that script done. It may be useful for others in a similar situation, or just to check your own development with one quick command.

I'm thinking of adding the ability to get tidy to fix what it can for xml and html files, but it would need to be an optional thing and not the default.

[http://paste.ubuntu.com/1029032/](http://paste.ubuntu.com/1029032/)

---

### Post by Lars Noodén on 2012-06-07
You might look into doing the (X)HTML validation in two passes.  First, ensure that the file is converted to XHTML.  Then, check that it is valid.

---

### Post by stobbsm on 2012-06-08
Update: Started to look into Graphviz, and discovered linkchecker will export to a dot file.

Problem: I get no information from what Graphviz makes. Any idea how to get linkchecker to generate what the pages are actually linking to? I would like to see what leads to a real page and what leads to a broken link.

I may be blind, but I haven't seen where in the linkchecker man page you can configure it to show the relationships between pages, instead of a just a list of all the assets on a page.

---

### Post by fatality_uk on 2012-06-08
> **stobbsm said:**
> Update: Started to look into Graphviz, and discovered linkchecker will export to a dot file.

Problem: I get no information from what Graphviz makes. Any idea how to get linkchecker to generate what the pages are actually linking to? I would like to see what leads to a real page and what leads to a broken link.

I may be blind, but I haven't seen where in the linkchecker man page you can configure it to show the relationships between pages, instead of a just a list of all the assets on a page.

What are your JavaScript/Jquery/PHP skills like?
If you have time, look here:

[http://simplehtmldom.sourceforge.net/](http://simplehtmldom.sourceforge.net/)

```
// Find all links 
foreach($html->find('a') as $element) 
       echo $element->href . '<br>';
```

*echo* your output to say a JSON object, then use JS/jQuery to load that link from the JSON array and pass that back to the PHP function to grab each link in each page.

Store the whole thing in a javascript array and even output to a text file or DB.

Hope this helps. If I had anytime, I would offer to take a look but right now, pretty snowed under.

---

### Post by stobbsm on 2012-06-09
I will look into that for sure! Could be great for future projects.

I've got linkchecker creating proper dot files not, and being processed into ps files.

Problem with this is that I don't care about images, css or scripts at the moment. Just the validity of anchors.

Any idea how to make linkchecker or dot ignore all the cruft, so I can make a good solid map?

---

### Post by stobbsm on 2012-06-13
> **fatality_uk said:**
> What are your JavaScript/Jquery/PHP skills like?
If you have time, look here:

[http://simplehtmldom.sourceforge.net/](http://simplehtmldom.sourceforge.net/)

```
// Find all links 
foreach($html->find('a') as $element) 
       echo $element->href . '<br>';
```

*echo* your output to say a JSON object, then use JS/jQuery to load that link from the JSON array and pass that back to the PHP function to grab each link in each page.

Store the whole thing in a javascript array and even output to a text file or DB.

Hope this helps. If I had anytime, I would offer to take a look but right now, pretty snowed under.

After being let down horribly by link checker, as it checks EVERY url or href reference (pictures, css and imported scripts included), I could not get a decent map.

I am now writing a script using simplehtmldom in PHP, running on the command line for now. It is using a combination of php and linkchecker in a bash script (hacky, I know) to build a valid dot file to generate a decent map without all the extra crap.

I will basically be making a bunch of extra files with everything that is not a link, ensuring the titles match the original file names, to generate myself a good list of links.

Anybody confused yet?

---

