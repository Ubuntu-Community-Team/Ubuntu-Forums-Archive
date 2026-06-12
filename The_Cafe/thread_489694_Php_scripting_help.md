---
title: "Php scripting help"
date: 2007-07-01
forum: The Cafe
---

### Post by tmatt95 on 2007-07-01
Over the holiday I am working on a pet project to create an dell "idea storm" like website as a project. There is one problem with a script that I found on the internet and that is that it is designed to look like digg. A great website but I would like it so that the user submits ideas and not websites. I have tried editing the php file but every time I do that I get a script error. Below is a link to the demo of the script I am using:
[http://demos.kubelabs.com/PHPDug/](http://demos.kubelabs.com/PHPDug/)

I have also attached the script that I think needs changing to this message.

If you know a script that work more like the idea storm and like digg, it would be great if you would submit it.

Regards,

Matt

---

### Post by kebes on 2007-07-01
> **tmatt95 said:**
> I have tried editing the php file but every time I do that I get a script error.

Can you be more specific about the errors? When you put a copy of the script in your web directory (save it as /var/www/add_story.php), then you should be able to go to the page:
[http://localhost/add_story.php](http://localhost/add_story.php)

Does that work? If you get an error, what is the error? For PHP scripts to work, you need to have PHP installed in your webserver (and then restart the server). Have you done that?

---

### Post by tmatt95 on 2007-07-01
> **kebes said:**
> Can you be more specific about the errors? When you put a copy of the script in your web directory (save it as /var/www/add_story.php), then you should be able to go to the page:
[http://localhost/add_story.php](http://localhost/add_story.php)

Does that work? If you get an error, what is the error? For PHP scripts to work, you need to have PHP installed in your webserver (and then restart the server). Have you done that?

Thanks for the quick reply. The problem with the script is that when the user clicks on the "submit a story" button on the main page, they are asked to supply an URL before adding the story. I want to skip this stage and go straight to adding the story. I have tried removing sections of the script but this bring in "syntax errors"

Regards,

Matt

---

### Post by kebes on 2007-07-01
Ah... so it's a PHP-coding issue. What specific change did you make, and what was the error?

Looking at the code, it seems to me that bypassing the URL checking could be accomplished by changing this code:
```

// Check if a url has been submitted
if(isset($_POST['story_url']))
{
	if(!preg_match('/^(http|https|ftp):\/\/([A-Z0-9][A-Z0-9_-]*(?:\.[A-Z0-9][A-Z0-9_-]*)+):?(\d+)?\/?/i',$_POST['story_url']))
	{
		$page = new HtmlTemplate ("templates/" . $config['tpl_name'] . "/add_story_step1.html");
		$page->SetLoop ('CATS', $cats);

```
To be like:
```

// Check if a url has been submitted
if(true)
{
	if(false)
	{
		$page = new HtmlTemplate ("templates/" . $config['tpl_name'] . "/add_story_step1.html");
		$page->SetLoop ('CATS', $cats);

```

That is, I'm just skipping the check by using "true" and "false".

---

### Post by ~LoKe on 2007-07-01
Why even use an if statement if there are no conditions?

```
$page = new HtmlTemplate ("templates/" . $config['tpl_name'] . "/add_story_step1.html");
$page->SetLoop ('CATS', $cats);
```

---

### Post by kebes on 2007-07-01
> **~LoKe said:**
> Why even use an if statement if there are no conditions?

Indeed. I just meant to try switching to "if(true)" and see if that fixes the problem. If so, then those statements can be entirely removed.

---

### Post by tmatt95 on 2007-07-02
Thank you for everyones help. It now works really well and does not ask for a website taking the user to the second part of submitting a story. 

Regards,

Matt

---

