---
title: "A command line Google Dictionary"
date: 2010-10-09
forum: The Cafe
---

### Post by Shadyabhi on 2010-10-09
Well, this is not done using google's API. Its a simple bash script that takes a word to be searched as parameter...

Its a very simple bash script, nothing fancy. **It shows word meaning, usage, various meanings from different sources, pronunciation, synonyms.** 

Steps involved in fetching the meaning:-

   1. Use curl to fetch the page's HTML
   2. Pipe it to html2text that converts to text.
   3. The returned test is saved to $HOME/dict.
   4. Also. a history file is made named $HOME/dict/dicthistory


The script saves all the meanings in /dict folder in home directory. If the folder is not present, then its created.

For more details:- [http://linux-junky.blogspot.com/2010/10/google-dictionary-command-line-version.html](http://linux-junky.blogspot.com/2010/10/google-dictionary-command-line-version.html)

```

dict() { 
if [ ! -d $HOME/dict ];then 
mkdir $HOME/dict;
fi
cat $HOME/dict/dicthistory | grep " $1$" 1>/dev/null 2>/dev/null;
if [ $? -eq 0 ]
then
	less $HOME/dict/$1;
	return;
fi
	echo `date`" -> ""$1" >> $HOME/dict/dicthistory;
	curl -s "http://www.google.com/dictionary?aq=f&langpair=en|en&q="$1"&hl=en" | html2text -nobs | sed '1,/^ *Dictionary\]/d' | head -n -5 > $HOME/dict/$1;
	stat_data=`stat $HOME/dict/$1 -t | awk '{print $2}'`
	echo -n "Bytes transferred: "
	echo $stat_data
	sleep 1;
	less $HOME/dict/$1;
	echo "::Last searched words.."
	cat $HOME/dict/dicthistory;
}
dictdelete()
{
	rm $HOME/dict/$1;
	cat $HOME/dict/dicthistory | grep -v " $1$" > $HOME/dict/dicthistory.bk;
	mv $HOME/dict/dicthistory.bk $HOME/dict/dicthistory;
	echo ":: Requested item $1 successfully deleted";
}
```

Paste this in /home/your_username/.bashrc file at the end. And now open new terminal and type $dict word

to see the word meaning.
To delete a word: $dictdelete word

---

### Post by Kingsley on 2010-10-28
This script is pretty cool. Thanks. I modified it so I only have to type 'd' since I'm a bit lazy. :D

---

### Post by Shadyabhi on 2010-10-28
Just updated the script. Its better now

---

### Post by ncwilde43 on 2010-11-09
Instead of creating a file for each definition, I just fetch the text and display it.  I've also added [FONT="Courier New"]less[/FONT] to the end of the command for better viewing.

```
function define {
    curl -s "http://www.google.com/dictionary?aq=f&langpair=en|en&q="$1"&hl=en" | html2text -nobs | sed '1,/^ *Dictionary\]/d' | head -n -5 | less
}
```

Thanks for the code!

---

### Post by Shadyabhi on 2010-11-09
> **ncwilde43 said:**
> Instead of creating a file for each definition, I just fetch the text and display it.  I've also added [FONT="Courier New"]less[/FONT] to the end of the command for better viewing.

```
function define {
    curl -s "http://www.google.com/dictionary?aq=f&langpair=en|en&q="$1"&hl=en" | html2text -nobs | sed '1,/^ *Dictionary\]/d' | head -n -5 | less
}
```

Thanks for the code!

I too used **less** in my code. BTW, the sole reason for saving all my fetched words on the local folder was because I am on a slow connection so even fetching just text becomes expensive.

So, in case, I forget the exact meaning of the word I learnt the other day, I could simply retrieve from the local file rather than downloading again from the web.

---

