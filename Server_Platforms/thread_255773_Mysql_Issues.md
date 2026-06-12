---
title: "Mysql Issues"
date: 2006-09-12
forum: Server Platforms
---

### Post by WagnerVaz on 2006-09-12
Hi all, I got some mysql issues. I'v tried XAMPP and standard ubuntu package.
I use phpmyadmin to easy administration during develop.

The problem is:
I go to phpmyadmin and add a new row to table, it's OK, do just fine. 
BUT, when I display it on the browser it just show as wrong charters, if I specify as UTF-8 (in the HTML code) the data from DB show as wrong charters. If I use ISO-8859-1 (in the HTML code) the data from DB show fine, but the static data in html show wrong. I know it is a bit crazy, but is sad :( 

Some example:
(H1 With UTF-8)
Descrição

(H1 With ISO-8859-1)
DescriÃ§Ã£o

(DB Text With UTF-8)
Ol&#65533;, este &#65533; um teste para testar fazendo um teste, vou digitar agora uma s&#65533;rie de ac&#65533;ntos. &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;

(DB Text With ISO-8859-1)
Olá, este é um teste para testar fazendo um teste, vou digitar agora uma série de acêntos. áéíóúçàèìòùãõ


So it is an BIG problem for me, I alredy do ANYTHING that I can do. Tried change file with iconv (the html file and the dump file)
Change the collation of DB, table and Field.

I cant figure what the hell is happening.

Can someone give a try?


Thanks soo mutch (even if you are just reading)

---

### Post by WagnerVaz on 2006-09-12
**Solved**
I just dig some more on google and find one solution:

After you make the php connection to the mysql, just execute these query:
[PHP]
mysql_query("SET CHARACTER SET 'utf8'");
[/PHP]

So I set these to utf8, but can be latin1, latin2 ... etc.

Thanks

---

