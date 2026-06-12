---
title: "Removing Unread Skype Chat Messages"
date: 2008-09-17
forum: The Cafe
---

### Post by SuperMike on 2008-09-17
I had a major blunder last night with Ubuntu and Skype, and I fixed it, so I wanted to share.

I'm sort of new to Skype on Ubuntu, and hadn't really focused on learning the ins and outs of it that much. A friend popped open a chat for me and I chatted him back. Well, somehow I ended up clicking the wrong name and sent the chat to an offline person -- BUT THE WRONG PERSON!

In my particular case, I was sending company confidential information to the wrong individual and it was CRITICAL I get it back. I noticed that this person was not online -- their icon was greyed out.

Well, on Windows and Mac, Skype has a way to remove and even edit unread chats. But Linux doesn't come with that.

The fix was that I had to shut down Skype, rename ~/.Skype to ~/.Skype.OLD, then fire up Skype again and relogin. The chats were gone.

To my surprise, THIS WORKED! The other person did not receive those chats because (a) he was offline, and (b) the chats did not get sent to him yet and were stored locally on my system. Evidently Skype doesn't officially send chats when someone is offline, and doesn't cache them up at the central Skype server. I then ran a test with a friend and we confirmed this is correct. His computer never showed the new chats.

Hope this helps you if you ever get in a bind like I was!

---

