---
title: "bash equivalent  preg_match_all"
date: 2015-01-28
forum: Ubuntu Application Development
---

### Post by iacoposk8 on 2015-01-28
hello everyone! how to translate this code in pure bash?
```

php -r '
    preg_match_all("/<table class=download>(.*?)<\/table>/",$argv[1],$tab); 
    preg_match_all("/<td>Linux<\/td>(.*?)<\/td>/",$tab[1][0],$rows);
    preg_match_all("/href=(.*?)>/",$rows[1][0],$a);
    echo $a[1][0];
' -- "$content"

```

---

### Post by schragge on 2015-01-28
Parsing HTML with bash/sed/awk is rather complicated and very error-prone. Better do it with a real scripting language like perl/python/ruby. They have special library modules for this. If you insist on doing it with sed then at least install something like [xml2]("http://manpages.ubuntu.com/manpages/trusty/en/man1/xml2.1.html") and parse its output.
```

echo "$content" |
html2 |
sed -n '\%.*/table/@class=download$%,$!d;/\/td=Linux$/,$!d;\%.*/td/.*/@href=%{s///p;q}'

```

---

### Post by iacoposk8 on 2015-01-28
tells me that the command HTML2 not installed ... and I do not find even with apt-get install.
 if I remove that line but the regular expression did not return any results

---

### Post by schragge on 2015-01-28
html2 is part of xml2 package
```
sudo apt-get install xml2
```

---

### Post by iacoposk8 on 2015-01-29
ok, now it gives me syntax errors html. the code I am using is this:
```

content=$(wget http://developer.android.com/sdk/index.html#Other -q -O -)

echo "$content" |
html2 |
sed -n '\%.*/table/@class=download$%,$!d;/\/td=Linux$/,$!d;\%.*/td/.*/@href=%{s///p;q}'

```

---

### Post by schragge on 2015-01-29
*html2* is rather picky about HTML syntax. Try it this way
```

content=$(wget -q -O - http://developer.android.com/sdk | sed '/ id="Other"/,$!d')
echo "$content" |
html2 2>/dev/null |
sed -n '\%.*/table/@class=download$%,$!d;/\/td=Linux$/,$!d;\%.*/td/.*/@href=%{s///p;q}'

```

Or, if you don't have to keep $content around for later use
```

wget -q -O - http://developer.android.com/sdk |
sed '/ id="Other"/,$!d' |
html2 2>/dev/null |
sed -n '\%.*/table/@class=download$%,$!d;/\/td=Linux$/,$!d;\%.*/td/.*/@href=%{s///p;q}'

```

And I guess in this particular case you could also get away with something as simple as
```

wget -qO- http://developer.android.com/sdk |
egrep -om1 'http[^"]+sdk[^"]+linux[^"]+'

```

The last one can actually be rewritten in *pure bash* as you requested:
```

pattern='http[^"]+sdk[^"]+linux[^"]+'
wget -qO- http://developer.android.com/sdk |
while read -r line
do
    [[ $line =~ $pattern ]] && printf %s\\n "$BASH_REMATCH" && break
done

```

---

### Post by iacoposk8 on 2015-01-30
works perfectly, thanks

---

