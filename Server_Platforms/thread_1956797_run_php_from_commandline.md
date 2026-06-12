---
title: "run php from commandline"
date: 2012-04-11
forum: Server Platforms
---

### Post by ZenMasta on 2012-04-11
What do I need to do to my server to allow a user to run a php script from console?

ie $ php myfile.php -- options

found the answer

sudo apt-get install php5-cli   :)

---

### Post by Jonathan L on 2012-04-12
Hi

If this is your first go at command-line PHP, there might a couple of other things you need which can be tricky to find out.

If you want to run the command like this:
```
$ mything options
```You need

[LIST]
[*] The file to be findable: call your file 'mything' and put it in a place in your path: typically ~/bin/mything or more rarely /usr/local/bin/mything
[*] The file to be executable: chmod 775 ~/bin/mything
[*] File must begin with special 'hash-bang' line: #!/usr/bin/php
[*] Your options are accessible in the array $argv
[/LIST]
 
Example file in ~/bin/showargv
```
#!/usr/bin/php
<?
print_r($argv);
?>
```And this is it running

```
$ showargv one two three
Array
(
    [0] => /home/username/bin/showargv
    [1] => one
    [2] => two
    [3] => three
)
```Hope this helps someone.

Kind regards,
Jonathan.

---

