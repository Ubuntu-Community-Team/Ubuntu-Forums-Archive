---
title: "PDF Word document search engine"
date: 2011-10-29
forum: Server Platforms
---

### Post by russelcouts on 2011-10-29
Hi all,
      I want to develop a PDF Word search application in PHP that will be executed under a Linux env. 
Could you advise me about a very good search engine to use.
TIA
Marco

---

### Post by SeijiSensei on 2011-10-29
Even though it's old, [htdig]("http://www.htdig.org/") remains an excellent search engine.  It returns results reasonably quickly, and it can index a wide array of documents including PDF files using external file converters like [pdftotext]("http://packages.ubuntu.com/lucid/poppler-utils").  I use htdig to index the archives of some private listservers I maintain.  Some of these have been in operation over a decade and have tens of thousands of messages.  I just ran a query against the biggest database for a word that appeared in about 10% of the indexed files.  It took about 25 seconds on my Linode VM.  Not very impressive if your standard of comparison is Google of course, but not unreasonable either.  Subsequent searches are faster because the index database has been cached by the operating system.  Putting all the databases on a RAM disk would probably improve performance.

For flat out speed, I don't think you can beat [Sphinx]("http://sphinxsearch.com/"), but it expects the documents to be stored in an SQL database.  I used it to index a product catalog with 40K items and was amazed at how quickly it returned results.  For PDFs, you might be able to create an indexing application that extracts the text with pdftotext and stores it alongside the actual documents in the database.  Then you could run Sphinx against the extracts.

Both of these are in the Ubuntu repositories.  

```
sudo apt-get install htdig
sudo apt-get install sphinxsearch
```

---

### Post by HermanAB on 2011-10-29
Howdy,

Most of what you want already exists.  Look in the repos for something called pdfgrep or some such.

---

### Post by SeijiSensei on 2011-10-30
> **HermanAB said:**
> Most of what you want already exists.  Look in the repos for something called pdfgrep or some such.

If he has a large database of documents, that approach will not perform as well as one that uses an index.  Grepping for a particular text string through tens of thousands of documents can take quite a while.  Also what happens when you're looking for more than one non-adjacent word, or a phrase, or want to do a Boolean search?  How would you weight the documents returned by grep according to relevance?  All these are features of search indexes like those I described above.

---

### Post by Lars Noodén on 2011-10-30
You can take a look at [Swish-e](http://swish-e.org/) for your web site.  It will index PDF and it is easy to set up.  Swish-e is in the Ubuntu repositories.

For larger projects you might also look at [Lucene](http://lucene.apache.org/) (or derivatives) and [Xapian](http://xapian.org/).

---

### Post by HermanAB on 2011-10-30
How often do you search?  If you look for something once a year, then grep is fine.

---

### Post by SeijiSensei on 2011-10-30
> **HermanAB said:**
> How often do you search?  If you look for something once a year, then grep is fine.

This sounded like a project for an organization, not an individual, where indexing would be much more valuable.

> **Lars Noodén said:**
> You can take a look at [Swish-e](http://swish-e.org/) for your web site.  It will index PDF and it is easy to set up.  Swish-e is in the Ubuntu repositories.

For larger projects you might also look at [Lucene](http://lucene.apache.org/) (or derivatives) and [Xapian](http://xapian.org/).

I tried swish-e when I first started indexing that listserver archive I mentioned above.  Once I discovered htdig I switched to that; I found it much more powerful than swish-e.

Lucene's heavy dependence on Java sent me looking for other solutions like Sphinx.  I've heard of Xapian but have not tried implementing it.

---

### Post by russelcouts on 2011-10-30
You are right it's a project for an organization for which indexing should be fast because tipically users will conduce search through a sequence of consecutive search.

---

### Post by SeijiSensei on 2011-10-30
I'll reiterate my earlier suggestion, then, that you build an archiving application that places the textual abstracts of the documents into a database, then index that with Sphinx.  You don't need to put the documents themselves in the database; you can just store pointers to their locations in the file system.  A typical record might have the file's full name including its path and the textual extract.  Index the abstracts with Sphinx and have it return the matching filenames.

---

### Post by Vegan on 2011-10-30
while there are a few projects around, implementing a PDF search will be brutal

I do not use PDF except for the scanner and OCR anymore

All my content is HTML of one dialect or the other

Today its HTML5 until the next update is published down the road

if you could grep common search terms into a XML or SQL database then over time it would become faster

---

### Post by Lars Noodén on 2011-10-30
> **SeijiSensei said:**
> I'll reiterate my earlier suggestion, then, that you build an archiving application that places the textual abstracts of the documents into a database, then index that with Sphinx.  You don't need to put the documents themselves in the database; you can just store pointers to their locations in the file system.  A typical record might have the file's full name including its path and the textual extract.  Index the abstracts with Sphinx and have it return the matching filenames.

That is more or less how the indexes above work.  Though they also allow for the indexing of keywords, not just full text.  ht://dig and Swish-e are easy enough to set up that it would not be worth duplicating the work by creating such a system from scratch except maybe as an exercise like for a thesis.

---

### Post by Jonathan L on 2011-10-30
> **russelcouts said:**
> develop a PDF Word search application in PHP

Hi Marco

If you actually want to do it yourself for some reason such as knowing about special words or names in your organisation or need unusual boolean operators, I'd consider converting the files with pdftotext and then indexing.  pdftext is part of poppler-utils, which you can install with apt-get.

When you index or reindex depends entirely on how often your PDF files change or are added.  It's normal to use a database (eg MySQL) for this, but it all depends on your circumstances.  It's similar in many ways to the problem of thumbnailing images.

Here's an illustration using a file per search term:

File 'mkindex':
```
#!/bin/sh

for f in "$@"; do
    echo "$f"

    pdftotext "$f" - \
    | tr -sc A-Za-z0-9 '\n' \
    | tr A-Z a-z \
    | sort \
    | grep -v '^[0-9]' \
    | grep -v '^.$' \
    | uniq \
    > /tmp/INDEX

    mkdir -p index
    for w in `cat /tmp/INDEX`; do
        echo "$f" >> index/$w
    done
done
```That does all the hard word of grinding through the files.  When the user types something into your search page in PHP, you pull up the files for their search terms and find the intersection:

File: searchindex:
```
#!/usr/bin/php
<?

$terms = $argv;
array_shift($terms);

$results = array();;
foreach ($terms as $k => $term) {
    $list = array();
    if (file_exists("index/" . $term)) {
        $list = file("index/" . $term, FILE_IGNORE_NEW_LINES);
    }
    if (!$results) {
        $results = $list;
    } else {
        $results = array_intersect($results, $list);
    }
    printf("# %d files contain '%s' (%d)\n",
        count($list), $term, count($results));
}

sort($results);
print_r($results);

?>

```Indexing 200MByte took about five minutes; searching for three terms took about 50ms.

```
./mkindex /some/bucket/*.pdf
./searchindex please dog thanks
```Hope that's of some amusement: whether you'd get any good mileage out of your own system depends entirely on specialist knowledge about your documents and how people want to search for them, and your skills as a PHP coder.

Kind regards,
Jonathan.

---

