---
title: "where to find a web scraper for linux?"
date: 2008-01-18
forum: Server Platforms
---

### Post by whitenight639 on 2008-01-18
Hi peeps,

Im not skilled in app programming, and as I'm a proud ubuntu user I dont know where else to post this, I'm after a web scraper that will aggregate business names addresses and website urls, I'm not a spammer or anything all i want to do is convert a list of a certain type of business's from yell.com and convert them into a CSV or XML file, so the scraper / spider only needs to stay on yell.com not go running off all over the place, I know you can build your own spider but i dont have the time/ skills, there must be one available that i can use for this purpose,

let me know your thoughts, 


Thanks in advance

---

### Post by HermanAB on 2008-01-18
Hereyago:
$ wget yadda.yadda.yadda | grep -e "whatever"

---

### Post by whitenight639 on 2008-01-18
Thanks alot, im reading thru the wget documentation but i don't understand how to: 

A:) specify which elements of the page to get eg I want to capture everything inbetween <div class="businessDetails magicFix"> and </div> 

and save that as a comma seperated value in a txt file (by the way I dont know much about CSV file format I will read up in a min.) 

B:) how to tell it which CSV file to create, save. 

Any advice would be greatly appreciated!

---

### Post by HermanAB on 2008-01-18
You cannot retrieve a partial page.  Use wget to get the page and pipe it through a search utility such as grep, then send the output of that through sed or cut or something to narrow things down some more.

Cheers,

Herman

---

### Post by whitenight639 on 2008-01-18
yer i've worked that out, now im just manually saving the web pages and trying to use grep, 

I want to extract text between <example html tag> and </example html tag end> 

how do do that with grep? or is it not possible? 

I'm asking stupid questions I know but once i have a command or script set up it will be worth it. Thanks for putting up with me!

---

### Post by whitenight639 on 2008-01-18
i'll check out sed and cut thanks

---

### Post by HermanAB on 2008-01-18
Also google for awk examples.  Between wget, grep, sed and awk you can do anything, but it isn't easy.

---

### Post by koenn on 2008-01-19
> **whitenight639 said:**
> yer i've worked that out, now im just manually saving the web pages and trying to use grep, 

I want to extract text between <example html tag> and </example html tag end> 

how do do that with grep? or is it not possible? 

I'm asking stupid questions I know but once i have a command or script set up it will be worth it. Thanks for putting up with me!

try something like
```

# grep text between tags, including tags, and save to file
grep -io -r "<example html tag.*</example html tag end>" /dir/with/pages > outputfile

# remove the tags
sed -i  s/"<example html tag>"//g outputfile
sed -i  s/"</example html tag end>"//g outputfile


```
note that in the grep statement, you only use part of the opening tag, and use **.*** as wildcard
test this first, eg to check that the sed statements don't erase your files completely.

---

### Post by fozy on 2008-01-19
If you check out python's webscraping capabilities, I'm sure you'll find a solution.

---

### Post by whitenight639 on 2008-01-19
thanks keon and all

I've found that using lynx is good for stripping out html and leaving text, i cant find any documentation on it tho. 

lynx --dump htmlpage5.html > myfile5.txt


This thread is no1 on google for search terms "linux web scraper" ! 

I think i will (try) and write a python script its going to be a long night.

---

### Post by UbuWu on 2008-01-20
Python + [Beatiful Soup]("http://www.crummy.com/software/BeautifulSoup/") is perfect for these kind of jobs!

---

