---
title: "can't edit post or reply to own post"
date: 2017-10-15
forum: Resolution Centre
---

### Post by TE7 on 2017-10-15
Can't seem to edit my post or reply to my own post or start a new thread.

---

### Post by coffeecat on 2017-10-15
I can see nothing in your account settings that would prevent you from posting or editing one of your posts. Indeed, you started a new thread a little over two hours ago, here:

[https://ubuntuforums.org/showthread.php?t=2374363](https://ubuntuforums.org/showthread.php?t=2374363)

Has the problem started since you made that post?

Please be aware that there are restrictions that affect all users with some sections, and with some threads. Old threads are automatically closed and you will not be able to edit one of your posts within a closed thread, nor will you be able to reply to a closed thread. Similarly, there are some sub-forums that are now closed to new threads, or closed to all posting. The permissions vary depending on the circumstances. But in all major and current areas of the forum you should be able to post without restriction.

Please provide links to threads you cannot reply to, posts that you are unable to edit, and any sub-forum where you find you cannot start a new thread.

---

### Post by TE7 on 2017-10-15
Thread is [https://ubuntuforums.org/showthread.php?t=2374363](https://ubuntuforums.org/showthread.php?t=2374363). Can't reply to or edit post. Says "Forbidden - no access to server".

---

### Post by coffeecat on 2017-10-15
Hmmm. That's odd. We were having problems some time ago with forbidden messages, but I thought that Canonical IS had fixed that.

I can view that thread from my account, and can also view it if I am not logged in. Please try logging out and seeing if you can then view the thread while not logged in. Of course, you won't be able to post to it while not logged in, but I want to see if you still get the forbidden message from the same browser as you are using now. Then log in again and see what happens, and report back. In the meantime, I'll ask the other admins if they have any other ideas.

---

### Post by TE7 on 2017-10-15
Logged out. Can view post. Logged back in. Can't edit post. Still get "Forbidden" message.

---

### Post by coffeecat on 2017-10-15
Can you be a little more specific please. I've got the other staff thinking about this too and, hopefully, we'll narrow down where the problem is.

So - while logged in as TE7.

[list=1][*]If you click on your link in post #3 here, can you see the thread? Yes or No. Do you get the error message then.
[*]If you can view the thread OK, click on the edit button. Don't do anything else. Do you get the forbidden message then?
[*]If you don't get the forbidden message when you simply click on the edit button, try an edit and then a save. Is that when you get the error message? By the way, I see that you successfully made 4 edits within a half hour of your original post.
[*]If you are getting the error message when saving, what is the nature of the edit? If you try to add too much material, or there are certain strings which trigger the firewall, you may get an error then.
[*]Last question for now. At that thread, what happens when you click on the ornage reply to thread button?[/list]

---

### Post by coffeecat on 2017-10-15
Sorry - typo in my previous post. That should have been "orange reply to thread button".

As a matter of policy, we don''t edit posts in this section.

---

### Post by TE7 on 2017-10-15
Clicking on link lets me view thread. New reply using orange button gets Forbidden. Yes I was able to edit the post several times before. Then I tried to edit it and post a lengthy code snippet. That's when the problems started. I also tried to post a new thread withe same topic in Desktops, but it wouldn't let me post new thread also.. As it is now I can't post or or reply or edit anything.

---

### Post by TE7 on 2017-10-15
I can post in this forum.

---

### Post by TE7 on 2017-10-15
Error: 

Forbidden

You don't have permission to access /editpost.php on this server.

Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443

---

### Post by coffeecat on 2017-10-15
> **TE7 said:**
> New reply using orange button gets Forbidden. 

When??!! I asked you to be specific, please. We cannot troubleshoot this without a clear description.

Do you get the forbidden message as soon as you click on the orange button, or only after you try to post some text? If only after you try to post some text, is this the "lengthy code snippet", or something else?

> **TE7 said:**
> Then I tried to edit it and post a lengthy code snippet.

I think this may be the problem, but I can't be sure because I can't tell whether you are getting a forbidden message with something else other than the "lengthy code snippet". As I said earlier, certain lengthy material can trigger the firewall.

> **TE7 said:**
> I also tried to post a new thread withe same topic in Desktops, but it wouldn't let me post new thread also..

With what? The "lengthy code snippet" or something else? I am trying to determine whether you simply can't post a new thread of any sort, or whether it's the lengthy code snippet that is the problem.

> **TE7 said:**
>  As it is now I can't post or or reply or edit anything.

Anything?? Have you tried to post something that doesn't involve the "lengthy code snippet"? I see that you can post in the Resolution Centre, so please start a new thread anywhere in one of the support forums with the title "test" and just the text "test". That way we can make sure nothing funky is happening with your forum account. If successful, one of the staff will remove it from public view.

After that, please try a trivial edit that doesn't involve the "lengthy code snippet" in the post that you are trying to edit now. Add a single character right at the very end of the post after the second code box. For example, the letter z - we can always take it out later. Please report back on what happens.

---

### Post by oldos2er on 2017-10-15
> **TE7 said:**
>  Then I tried to edit it and post a lengthy code snippet. 

We've had some problems in the past with "lengthy" (40KB or more, don't remember the exact figure) code posting. The solution is to use paste.ubuntu.com and add the link to your post.

This sounds like it's only part of your problem however.

---

### Post by coffeecat on 2017-10-15
Hello, TE7. The staff has been having a discussion about this, and there is another possibility apart from a lengthy stretch of code that might be the problem. 

Question. Are you trying to post html code, and/or are you trying to post this string in your edit:

```
< h t m l >
```

But without the spaces. If you do that, you will get the forbidden message that you are seeing. This is a security measure. If this is what you are doing and you need to post some html code with that string, please use paste.ubuntu.com with a link in your post as oldos2er suggests.

---

### Post by TE7 on 2017-10-15
I was able to edit original post and add z. Created a test new thread post here [https://ubuntuforums.org/showthread.php?t=2374391&p=13698237#post13698237](https://ubuntuforums.org/showthread.php?t=2374391&p=13698237#post13698237)

---

### Post by TE7 on 2017-10-15
Was not able to create new lengthy post.

---

### Post by TE7 on 2017-10-15
Maybe my original post plus the code snippet edit addition just made the original post too long. Maybe why I couldn't create a new lengthy post. Too long.

---

### Post by coffeecat on 2017-10-15
Did you read my post at #13? There was a question in it.

---

### Post by TE7 on 2017-10-15
No html code of any sort. Just the post explanation plus 3 different ```

``` sections.

---

### Post by TE7 on 2017-10-15
3 different code sections using the ```
 block tags
```

---

### Post by TE7 on 2017-10-15
The code blocks had XML code in some of them, including the original code snippet I was trying to add to the original post by editing.

---

### Post by cariboo on 2017-10-15
Why not create a new post with the additional information?

---

