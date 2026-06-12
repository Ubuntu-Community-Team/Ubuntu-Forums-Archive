---
title: "[SOLVED] PHP5 parsing on Ubuntu Linux 8.04 (AMD64)"
date: 2008-06-25
forum: Server Platforms
---

### Post by Chris_TH on 2008-06-25
Hi,

A tiny problem with Apache2/PHP5 parsing.

I'm using Sarissa on my LAMP server. As all my js, Sarissa also has a tiny PHP header, classifying the js.
This means that the js is parsed by the PHP parser before being sent to the client browser.
All other js works fine, but Sarissa gives me a problem. When the parser reaches the following statements it reports a parsing error:

        else {
            var oDoc = new ActiveXObject(_SARISSA_DOM_PROGID);
            if (s.substring(0, 5) == '<?xml') {
                s = s.substring(s.indexOf('?>') + 2); 
            }

I have identified that the PHP5 parser picks up: '<?xml' and '?>' as the start/end of an XML block (which it is not, they are tokens).

How do I make PHP5 aware of that fact that they are tokens? The same code (complete website) runs without errors on a non-Ubuntu distribution. (I have tried a few variants, but always with the same result: A parsing error).

---

### Post by hyper_ch on 2008-06-25
(1) when posting a piece of code, use [noparse]```

```[/noparse] tags, or even better [noparse][php][/php][/noparse]  --> that makes it a lot easier to read.

(2) and this doesn't look to me like PHP, it looks like JS. Without seeing the whole code I can't really help there.
[php]
else
{
    var oDoc = new ActiveXObject(_SARISSA_DOM_PROGID);
    if (s.substring(0, 5) == '<?xml')
    {
        s = s.substring(s.indexOf('?>') + 2);
    }
[/php]

---

### Post by Chris_TH on 2008-06-25
Yes, as I wrote it is Sarrissa which is js. I have the following code added in the header that triggers PHP:

[php]
<?php
define('PROJECT_ROOT_DIR', realpath(dirname(__FILE__).'/../../../../..'));
define('PROJECT_NAME', 'cb');
define('APP_NAME', 'internet');
define('PAGE_TYPE', 'JS');

require_once(PROJECT_ROOT_DIR.'/site/lib/common.php');

header('Content-Type: text/javascript; charset=UTF-8');

header('Cache-Control: must-revalidate');
header('Expires: '.gmdate('D, d M Y H:i:s', time() + CSSJS_OFFSET).' GMT');
?>
[/php]

Then follows the original Sarissa js. The PHP5 parser ought to parse correctly, but ends up "plucking" an XML block out of the js text.

---

### Post by cdenley on 2008-06-25
I think I understand. Try this
[php]
else
{
    var oDoc = new ActiveXObject(_SARISSA_DOM_PROGID);
    if (s.substring(0, 5) == '<?print '<?';?>xml')
    {
        s = s.substring(s.indexOf('<?print '?>';?>') + 2);
    }
[/php]

---

### Post by Chris_TH on 2008-06-25
I'll try it out. Thank you.
But I still think that there ought to be a standard to prevent faulty parsing. (like: always put a string constant in double qoutes to prevent parsing!). I tried that and it does also not solve the problem. At the moment I work with "meta" characters and use &lt and &gt as substitutes for < and >, but I have not come to the point where I know that it works,

---

### Post by cdenley on 2008-06-25
cat test.php
[php]
else
{
    var oDoc = new ActiveXObject(_SARISSA_DOM_PROGID);
    if (s.substring(0, 5) == '<?print '<?';?>xml')
    {
        s = s.substring(s.indexOf('<?print '?>';?>') + 2);
    }
[/php]
php test.php
```

else
{
    var oDoc = new ActiveXObject(_SARISSA_DOM_PROGID);
    if (s.substring(0, 5) == '<?xml')
    {
        s = s.substring(s.indexOf('?>') + 2);
    }

```
I guess I don't understand what your problem is, then. What output are you expecting from that piece of code?

---

### Post by Chris_TH on 2008-06-25
Well, the javascript code follows the PHP header. If the PHP parser is clever enough it would determine when a <?xml is a parameter to a function or if it is in fact a "breakout" of the javascript (like injecting a PHP variable).

I dont know if I have not set up PHP5 correctly (or have something missing), or if the Ubuntu PHP5 module is missing some parsing functionallity (or if I dont follow the parser conventions). A PHP parser should pass everything on that is unrelated to PHP.

Like:

<?php

php block ......

?>

javascript (all text)


The php block should be processed and the text (that is in fact javascript code) should be passed on to the client browser.

If the PHP parser is not able to determine what is text to parse and what is text to pass on untouched, then I'm in big trouble.

In the resulting page the sarissa is just a plain include:

<script language="javascript" type="text/javascript" src="http://cbthailand.homeip.net/static/js/sarissa.js"></script>

The PHP parser picks it up due to the php code in the header, but continues to parse the remaining text ofter the php block has been closed.

I dont mind that, as long as it know what is what (text or text to process).

---

### Post by cdenley on 2008-06-25
Anything in between "<?" (or "<?php ") and "?>" will be interpreted as php code, regardless of the context. Everything else will be passed on as-is.

---

### Post by hyper_ch on 2008-06-25
it's time you give the full code.. with those fragments I can't see how they are connected and what you want...

---

### Post by Chris_TH on 2008-06-25
Well, it is basically the standard Sarissa.js, but with a PHP header. Here it is. The parsing fails in line 252.

---

### Post by Chris_TH on 2008-06-25
> **cdenley said:**
> Anything in between "<?" (or "<?php ") and "?>" will be interpreted as php code, regardless of the context. Everything else will be passed on as-is.

On the other distribution (I'll get the specifics), it does not happen. Everything is parsed without problems.

---

### Post by hyper_ch on 2008-06-25
and what' the exact error message you get?

---

### Post by Chris_TH on 2008-06-25
[Wed Jun 25 16:14:14 2008] [error] [client 122.162.105.181] PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /var/www/cb/site/web/internet/static/js/sarissa.js on line 252, referer: [http://cbthailand.homeip.net/landing.cb?l=en](http://cbthailand.homeip.net/landing.cb?l=en)

---

### Post by Chris_TH on 2008-06-25
> **cdenley said:**
> Anything in between "<?" (or "<?php ") and "?>" will be interpreted as php code, regardless of the context. Everything else will be passed on as-is.

So how do you prevent the parsing? If Sarissa needs to look for the beginning and end of the XML encapsulated DOM document, how do you do it without searching for the <?xml and the ?> tokens??

---

### Post by cdenley on 2008-06-25
> **Chris_TH said:**
> So how do you prevent the parsing? If Sarissa needs to look for the beginning and end of the XML encapsulated DOM document, how do you do it without searching for the <?xml and the ?> tokens??

I already showed you! Replace "<?" with "<?print '<?';?>" and replace "?>" with "<?print '?>';?>".

You can't stop it from looking for <?, but you can replace it with a php statement that prints the xml header.

---

### Post by Chris_TH on 2008-06-25
> **cdenley said:**
> I already showed you! Replace "<?" with "<?print '<?';?>" and replace "?>" with "<?print '?>';?>".

You can't stop it from looking for <?, but you can replace it with a php statement that prints the xml header.

Just tested it out and it works. A bit strange syntax (when the PHP parser should be able to parse javascript also), but for now I'm happy. Thanks a lot.

(BTW. I always thought that <?php was a trigger for php code and not a simple <?. Does that collide with the standards? What I mean, if an XML block starts with <?xml, how can you trigger on a simple <? ?)

---

### Post by cdenley on 2008-06-25
> **Chris_TH said:**
> 
(BTW. I always thought that <?php was a trigger for php code and not a simple <?. Does that collide with the standards?)

[http://www.php.net/manual/en/ini.core.php#ini.short-open-tag](http://www.php.net/manual/en/ini.core.php#ini.short-open-tag)

---

### Post by Chris_TH on 2008-06-25
> **cdenley said:**
> [http://www.php.net/manual/en/ini.core.php#ini.short-open-tag](http://www.php.net/manual/en/ini.core.php#ini.short-open-tag)

Well thank you one more time. I guess that the short_open_tag is set to true by default in the Ubuntu LAMP server. Now I know how to turn it off.

---

