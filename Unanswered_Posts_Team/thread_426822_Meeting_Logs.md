---
title: "Meeting Logs"
date: 2007-04-28
forum: Unanswered Posts Team
---

### Post by jpeddicord on 2007-04-28
Meeting logs have been moved to the wiki.

[https://wiki.ubuntu.com/UnansweredPostsTeam/Meetings](https://wiki.ubuntu.com/UnansweredPostsTeam/Meetings)

Please update your bookmarks.

---

### Post by jpeddicord on 2007-04-28
[B][B]Topics Covered:
[/B][/B][LIST]
[*]Possible options for marking unanswered posts
[*]Possibility of having the Thread Subscription box above the submit button, since many users will not see it when they post. Subscriptions make sure that the user knows their question is answered, and in turn reduces duplicate posts.
[*]Launchpad option for adding posts as bugs/answers.
[*]There was an idea to determine "unlucky" users that have many unanswered posts. However, it would be extremely server-intensive.
[*]Search links were discussed, as well as a method to determine if a bumped post was answered by the UA team.
[*]A meeting time was decided of 00:01 UTC on Sundays, once a month. The one-minute offset is to avoid confusion with midnight.[/LIST]****> [FONT=Courier New]Apr 28 19:58:57 <jacobmp92>    Welcome to the first meeting of the UF Unanswered Posts Team!
Apr 28 19:59:20 <jacobmp92>    let me pull up the agenda
Apr 28 19:59:37 <jacobmp92>    allrighty
Apr 28 20:00:15 <jacobmp92>    first off: congrats everyone on making it on the team, and for those not on the team yet, i'm looking forward to having you. :)
Apr 28 20:01:20 <jacobmp92>    next: For organizational purposes, we have a LP team, of which I'd like everybody to join if not on already.
Apr 28 20:01:21 <jacobmp92>    [https://launchpad.net/~ubuntuforums-unanswered]("https://launchpad.net/%7Eubuntuforums-unanswered")
Apr 28 20:02:32 <jacobmp92>    or better yet, [https://launchpad.net/~ubuntuforums-unanswered/+join]("https://launchpad.net/%7Eubuntuforums-unanswered/+join")
Apr 28 20:03:14 <RichardKut_>    Done
Apr 28 20:03:31 <jacobmp92>    and approved :)
Apr 28 20:03:55 <RichardKut_>    Thanks!!
Apr 28 20:04:16 <madmetal1>    i am not a team member..
Apr 28 20:04:20 <madmetal1>    can i join?
Apr 28 20:04:21 <madmetal1>    :)
Apr 28 20:04:46 <jacobmp92>    madmetal1: do a join request on the forums first, that way i can keep track of everybody. what's your forums account?
Apr 28 20:05:07 <madmetal1>    i have made a join request..
Apr 28 20:05:15 <madmetal1>    my forum account is madmetal
Apr 28 20:05:20 <jacobmp92>    oh wait, i see it, never mind :)
Apr 28 20:05:45 <madmetal1>    ;)
Apr 28 20:06:01 <jacobmp92>    ok madmetal1, you have been added to the group, now you can register on LP :)
Apr 28 20:06:11 <madmetal1>    oke :D
Apr 28 20:07:06 <jacobmp92>    added
Apr 28 20:07:22 <madmetal1>    i joined team on launchpad also
Apr 28 20:07:34 <jacobmp92>    yep, and approved :)
Apr 28 20:07:56 <jacobmp92>    Before I go any further, does anybody have any questions/suggestions for the team?
Apr 28 20:08:18 <RichardKut_>    Yes, I have a suggestion.
Apr 28 20:08:29 <jacobmp92>    ok, go ahead
Apr 28 20:08:56 <RichardKut_>    I would like to propose a change be made to the Ubuntu forums just for team members.
Apr 28 20:09:34 <RichardKut_>    I believe that we need a way to flag a post for promotion to other members attention.
Apr 28 20:09:47 <RichardKut_>    How do you guys feel about that?
Apr 28 20:10:05 <jacobmp92>    yes, i do think that would be handy
Apr 28 20:10:28 <kidders>    me too
Apr 28 20:10:56 <jacobmp92>    but the implementation is what might get difficult. ubuntu-geek would have to find a vBulletin plugin/script (or write one) for it
Apr 28 20:11:19 <RichardKut_>    Can we propose something like that to whoever manages the forum web site?
Apr 28 20:11:19 <adamtropics>    tags
Apr 28 20:11:26 <jacobmp92>    granted, we could just tag the posts as "ufua", but then anybody could tag it to get attention
Apr 28 20:11:44 <RichardKut_>    That is what I want to avoid.
Apr 28 20:11:50 <jacobmp92>    RichardKut_: i'll forward the request to ubuntu-geek. :-)
Apr 28 20:11:59 <RichardKut_>    Thanks!!
Apr 28 20:13:06 <jacobmp92>    another system that is possible;
Apr 28 20:13:26 <jacobmp92>    and would put less stress on the server (and ubuntu-geek ;))
Apr 28 20:13:45 <madmetal1>    well most unanswered post remain unansered for some reason so maybe a read-first post that will be clear and on top..
Apr 28 20:14:10 <RichardKut_>    How about a digest of the posts which could be e-mailed to team members?
Apr 28 20:14:16 <jacobmp92>    madmetal1: most users don't read the stickies :-/
Apr 28 20:14:21 <jacobmp92>    RichardKut_: good idea
Apr 28 20:14:34 <adamtropics>    like that one, yes
Apr 28 20:14:35 <madmetal1>    i know but if its in the main it would be better..
Apr 28 20:14:38 <jacobmp92>    and that might be able to be implemented with this:
Apr 28 20:14:52 <jacobmp92>    we could have an offsite location to have a database of marked posts,
Apr 28 20:15:20 <jacobmp92>    and i can whip up a firefox/greasemonkey extension to add a "Mark Post" button to the page/toolbar
Apr 28 20:15:38 <RichardKut_>    I do not believe that we should invest any significant amount of development effort into this.
Apr 28 20:15:42 <jacobmp92>    which would verify UA membership status, and then add it to a list
Apr 28 20:15:56 <RichardKut_>    We should keep it simple.
Apr 28 20:15:57 <jacobmp92>    RichardKut_: there are some systems that are premade for these situations
Apr 28 20:16:17 <jacobmp92>    plus i am a coding type :-P
Apr 28 20:16:22 <spd106>    What about adding a bug to the launchpad team?
Apr 28 20:16:23 <adamtropics>    launchpad for one!
Apr 28 20:16:33 <jacobmp92>    true, LP would work nicely
Apr 28 20:16:40 <RichardKut_>    OK, but I feel that all we need is a way to raise the visibility of a post selectively, and
Apr 28 20:16:49 <jacobmp92>    we could file a product under the team, and report bugs to it
Apr 28 20:16:58 <RichardKut_>    that should only be possible for our members.
Apr 28 20:17:01 <jacobmp92>    right
Apr 28 20:17:13 <adamtropics>    why?
Apr 28 20:17:24 <RichardKut_>    Elaborate...
Apr 28 20:17:32 <adamtropics>    why only members
Apr 28 20:17:52 <RichardKut_>    Because otherwise it would be self-serving to the poster.
Apr 28 20:18:03 <jacobmp92>    adamtropics: if we let anybody raise the priority of a post, or add a bug in a launchpad case, then everybody would be doing it.
Apr 28 20:18:11 <jacobmp92>    what RichardKut_ said. :)
Apr 28 20:18:35 <madmetal1>    yeap also agree to member only..
Apr 28 20:18:46 *    palmerthegeek (n=palmer@c-69-255-144-98.hsd1.va.comcast.net) has joined #ubuntuforums-unanswered
Apr 28 20:18:50 <adamtropics>    mmmm, disagree really, you have to trust users a little! but anyway...outvoted!
Apr 28 20:18:56 <RichardKut_>    How about we make this an action item for someone to follow thru on?
Apr 28 20:19:39 <jacobmp92>    as in the topics? or this issue as a whole?
Apr 28 20:19:59 <RichardKut_>    Let's find out what the possibilities are,
Apr 28 20:20:08 <RichardKut_>    otherwise the point is academic.
Apr 28 20:20:13 <madmetal1>    ok..
Apr 28 20:20:51 <madmetal1>    one request.. :) simple talking i am not speaking english natively :P
Apr 28 20:20:59 *    palmerthegeek (n=palmer@c-69-255-144-98.hsd1.va.comcast.net) has left #ubuntuforums-unanswered ("Ex-Chat")
Apr 28 20:21:11 <jacobmp92>    madmetal1: i never would have known :)
Apr 28 20:21:34 <RichardKut_>    No problem there...
Apr 28 20:21:54 <madmetal1>    its ok dont interrupt talk :) i am greek :P so move on with discussion
Apr 28 20:22:05 *    madmetal1 is now known as spyros
Apr 28 20:22:35 <RichardKut_>    Can we ask ubuntu-geek to research the possibilities? How do you feel?
Apr 28 20:23:06 <adamtropics>     quick question....is there a point in time at which we consider an unanswered post, a no longer interested item?
Apr 28 20:23:16 <adamtropics>    this is why btw, I think users should be able to post/flag on whatever new system is decided upon.
Apr 28 20:23:25 <RichardKut_>    Good question!
Apr 28 20:23:35 <adamtropics>    thank you!
Apr 28 20:23:39 <jacobmp92>    RichardKut_: i like the idea, and i will be asking him tomorrow/tonight, but I don't know what his response will be :)
Apr 28 20:24:22 <jacobmp92>    i don't know of a specific time to make a post uninterested, any thoughts?
Apr 28 20:24:37 <ajmorris_>    i think users should be able to flag their posts after a certain time of been unanswered has past otherwise we may never see them and they will stay unanswered
Apr 28 20:24:45 <spyros>    well time doesnt matter to me i think theme is more important..
Apr 28 20:25:17 <RichardKut_>    I believe that users orphan posts, they don't usually maintain them.
Apr 28 20:25:34 <jacobmp92>    ajmorris_: good point. if it goes unanswered too long, if they still cared, they could mark it. if they didn't care anymore (or found an answer) then they wouldnt bother to report it, so in that case it would work.
Apr 28 20:25:45 <adamtropics>    I can only speak for me, but I mean, after like a week, the point is either lost, or solved by other means, so perhaps attack it
Apr 28 20:25:56 <jacobmp92>    yeah
Apr 28 20:26:00 <adamtropics>    from both sides, and encourage people to return
Apr 28 20:26:01 <kidders>    ajmorris... users could just bump their posts, i suppose?
Apr 28 20:26:10 <adamtropics>    and say if help is required?
Apr 28 20:26:23 <ajmorris_>    and maybe mark the amount of urgency?
Apr 28 20:26:27 <RichardKut_>    Note: I have answered posts that were two weeks old, and the poster was grateful.
Apr 28 20:26:40 <jacobmp92>    yeah
Apr 28 20:26:56 <jacobmp92>    thing is, we need an easy, somewhat fast triage system to mark the posts
Apr 28 20:27:05 <RichardKut_>    We should ask the users permission to close the post,
Apr 28 20:27:11 <spd106>    Perhaps check subsequent posts by the same author?
Apr 28 20:27:12 <mojoman>    surprisingly few people bump their threads though so...
Apr 28 20:27:14 <adamtropics>    same here too, but pretty rare....although i guess it could still help someone else later.
Apr 28 20:27:15 <spyros>    the post that i wont ever think of no interest are those with hardware problems.. eg laptops and wireless
Apr 28 20:27:18 <jacobmp92>    Absolute Beginner Talk and certain support forums have an option to mark a topic as resolved
Apr 28 20:27:19 <ajmorris_>    it depends what the topic is, if they don't need it right away they would still be grateful after 2 weeks
Apr 28 20:27:23 <mojoman>    ...maybe letting users tag them isn't a bad idea?
Apr 28 20:27:24 <RichardKut_>    we did not open it, so we have no right to close it.
Apr 28 20:28:10 <adamtropics>    absolutely, but resources should be directed where they are most likely needed, which would surely be the more recent unanswered posts?
Apr 28 20:28:16 <jacobmp92>    mojoman: then people could still tag posts the moment they are made
Apr 28 20:28:47 <ajmorris_>    jacobmp92, set a time limit for when they can tag them
Apr 28 20:29:00 <ajmorris_>    like maybe 2 days?
Apr 28 20:29:11 <jacobmp92>    ajmorris_: again, something i would have to ask ubuntu-geek about, as he would have to code it.
Apr 28 20:29:17 <RichardKut_>    People who post do automatically subscribe to their post, right?
Apr 28 20:29:28 <adamtropics>    i hope so!
Apr 28 20:29:44 <jacobmp92>    many users don't know the option is there however.
Apr 28 20:29:52 <RichardKut_>    Maybe that should be automatic?
Apr 28 20:29:55 <adamtropics>    isn't it default
Apr 28 20:30:01 <spyros>    no its not..
Apr 28 20:30:17 <ajmorris_>    adamtropics, u can set it default in usercp i think
Apr 28 20:30:17 <spyros>    i also agree it must be set as default..
Apr 28 20:30:17 <RichardKut_>    Another proposed change?
Apr 28 20:30:24 <jacobmp92>    nope, but you can change that in profile options
Apr 28 20:30:42 <RichardKut_>    It should be default, I feel.
Apr 28 20:30:43 <jacobmp92>    RichardKut_: not many people want subscribe by default on a new account, me being one of them
Apr 28 20:30:58 <jacobmp92>    i only subscribe to certain threads if i am waiting for feedback
Apr 28 20:31:03 <spyros>    i suggest about subscribe to post should be default for the first 1-3 replies..
Apr 28 20:31:20 <adamtropics>    nice idea
Apr 28 20:31:25 <spyros>    so if there is a reply the user will be noticed
Apr 28 20:31:31 <jacobmp92>    but, say somebody goes to the cafe after making an account, then their posts are automatically subscribed
Apr 28 20:31:35 <spyros>    and if there are a lot the user wont have a mess of mails..
Apr 28 20:31:39 <RichardKut_>    Agreed. But provide the user an option after that to continue or not.
Apr 28 20:31:52 <spyros>    yeap
Apr 28 20:32:19 <jacobmp92>    maybe we could just have the Subscribe to this thread option more visible? ie. right above the Submit button?
Apr 28 20:32:19 <RichardKut_>    I am thinking to keep it simple and user-friendly, if possible.
Apr 28 20:32:28 <RichardKut_>    Yes!!
Apr 28 20:32:36 <spyros>    also agree..
Apr 28 20:32:41 <ajmorris_>    me 3
Apr 28 20:32:56 <adamtropics>    sorry, the reply notification stops if you don't visit the thread having been notified anyway so mail shouldn't stack up, plus there is an unsubscribe link in each notification mail.
Apr 28 20:33:11 <jacobmp92>    all right then. that is one that should be easy enough to implement, so I'll contact u-g with that one also :)
Apr 28 20:33:24 <RichardKut_>    Thanks.
Apr 28 20:34:11 <RichardKut_>    Question about the Launch Pad... OK?
Apr 28 20:34:21 <jacobmp92>    yep
Apr 28 20:34:47 <RichardKut_>    There is an Answers tab. Do we post common answers to posts there?
Apr 28 20:35:35 <adamtropics>    jacobmp92: since you're contacting him anyhow, how about a notification email if a thread has gone unanswered after a couple days, requiring a response to say if help is still needed?
Apr 28 20:35:45 <jacobmp92>    the Answers tab is a form in itself really. It could be used, however you cannot mark priorities and such
Apr 28 20:35:54 <RichardKut_>    Good idea!!
Apr 28 20:36:03 <RichardKut_>    Thanks Jacob.
Apr 28 20:36:08 <jacobmp92>    adamtropics: ok, i'll add that
Apr 28 20:36:42 <spyros>    agree with adamtropics about it..
Apr 28 20:36:44 <jacobmp92>    Bugs is basically like answers, but you can mark priorities and assign them to tasks
Apr 28 20:37:01 <RichardKut_>    Please define tasks...
Apr 28 20:37:26 <jacobmp92>    RichardKut_: tasks as in LP projects, milestones, etc
Apr 28 20:37:36 <jacobmp92>    not too useful in this case, but you never know :-P
Apr 28 20:37:51 <RichardKut_>    OK, can we link bugs to those tasks.
Apr 28 20:38:33 <jacobmp92>    okay, to recap
Apr 28 20:38:52 <jacobmp92>    1. Subscribe option above post button.
Apr 28 20:39:09 <jacobmp92>    2. 
Apr 28 20:39:13 <jacobmp92>    oops
Apr 28 20:39:22 <adamtropics>    RichardKut_ : Actually you reminded me that we can link forum posts to launchpad bugs now, that may help.
Apr 28 20:39:35 <jacobmp92>    2. Flagging old posts if left unanswered, requiring user input
Apr 28 20:40:02 <jacobmp92>    3. Launchpad Answers (or bugs) system for marking posts
Apr 28 20:40:22 <RichardKut_>    If all that can be done, then that is great progress in my mind!!
Apr 28 20:40:37 <jacobmp92>    :)
Apr 28 20:40:43 <kidders>    I also have a question, if that's okay. (I'll get in the queue hehe!)
Apr 28 20:40:47 <jacobmp92>    sure
Apr 28 20:41:15 <kidders>    (after you're done summarising) :-)
Apr 28 20:41:26 <jacobmp92>    nah i'm done :)
Apr 28 20:41:28 <kidders>    hehe
Apr 28 20:41:51 <kidders>    well, it's just that i sometimes answer threads by users who...
Apr 28 20:42:03 <kidders>    have posted multiple unanswered threads
Apr 28 20:42:35 <adamtropics>    you mean duplicate, or other questions?
Apr 28 20:42:40 <kidders>    consistently being ignored can give people a very negative impression of the forum/linux in general, etc...
Apr 28 20:42:48 <kidders>    sorry adam...
Apr 28 20:42:57 <kidders>    i meant both, really
Apr 28 20:43:13 <adamtropics>    ok, get it now...direct them to Aysiu (I think) sticky?
Apr 28 20:43:25 <kidders>    ahh
Apr 28 20:43:32 <spyros>    yeap also agree about negative impression thats why i am inderested into replying una posts..
Apr 28 20:43:46 <adamtropics>    all about why posts go unanswered....will find link
Apr 28 20:43:48 <RichardKut_>    I have sometimes had to stop offering support because of limits in my knowledge...
Apr 28 20:44:02 <jacobmp92>    well, if they ask a different question, then that is what our team is to solve. if it is a duplicate, then either do what adamtropics said or just post a link to the answered thread
Apr 28 20:44:03 <kidders>    it seems to me that one of the main purposes of our team is to make people feel less "ignored"...
Apr 28 20:44:16 <jacobmp92>    kidders: you got it
Apr 28 20:44:19 <RichardKut_>    but the poster usually appreciates the honesty and reposts differently to pursue a solution.
Apr 28 20:44:35 <kidders>    ... is it stupid to request a way of detecting multiple unanswered posts by the same user?
Apr 28 20:44:43 <RichardKut_>    No
Apr 28 20:44:48 <kidders>    (yeah richardkut... i agree)
Apr 28 20:45:03 <kidders>    (about users appreciating honesty)
Apr 28 20:45:14 <adamtropics>    you kind of can...if you click on the users name and then 'find all posts by ""'
Apr 28 20:45:15 <jacobmp92>    not a bad idea at all, and I believe an upgrade was just put in to check for those
Apr 28 20:45:29 <RichardKut_>    Cool!!
Apr 28 20:45:29 <kidders>    kewl :-)
Apr 28 20:45:35 <adamtropics>    given that it's normally newer users with only a few posts to sift through
Apr 28 20:45:45 <jacobmp92>    actually, it might have just been in the posting form, when you pick a title you get a "Check if already Posted" button
Apr 28 20:46:15 <kidders>    it would be great to be able to call up a list of users who haven't had much luck on the form...
Apr 28 20:46:20 <jacobmp92>    FYI: I believe everybody on this team has had search limits removed, so Find All Posts option would work pretty easily
Apr 28 20:46:23 <kidders>    ... they're the people we should be targeting, in many ways
Apr 28 20:46:28 <jacobmp92>    yeah
Apr 28 20:46:34 <kidders>    (kewl jacob... thanks)
Apr 28 20:46:38 <RichardKut_>    Statistics available for that?
Apr 28 20:47:16 <kidders>    that's exactly what i meant... thanks richard :-)
Apr 28 20:47:57 <jacobmp92>    i'm not sure how we can determine that. we could do a post search per user and see how many were unanswered, but again this would need hard-coded into the forums
Apr 28 20:48:26 <jacobmp92>    and by the looks of it, is looks pretty server-intensive, and someone would kill me for killing the server :-P
Apr 28 20:48:27 <RichardKut_>    Is there a database back-end to the forum?
Apr 28 20:48:30 <kidders>    yeah... it'd also make the server do a LOT of work :-(
Apr 28 20:48:37 <jacobmp92>    RichardKut_: yeah, its a standard MySQL
Apr 28 20:48:39 <kidders>    lol oops ditto
Apr 28 20:48:58 <jacobmp92>    :-P
Apr 28 20:49:06 <RichardKut_>    I can code SQL if you need...
Apr 28 20:49:30 <jacobmp92>    RichardKut_: its not the SQL problem, its just that ubuntu-geek is the only one with access to the database
Apr 28 20:49:46 <RichardKut_>    Bottleneck issue?
Apr 28 20:49:52 <jacobmp92>    a bit
Apr 28 20:50:23 <kidders>    being able to identify repeatedly "unlucky" posters would really help us make a difference to people (especially beginners) ... maybe it could be worth the effort?
Apr 28 20:50:24 <RichardKut_>    OK, maybe we could table the idea for later, cause I feel that it merits more exploration. How do you feel?
Apr 28 20:50:38 <RichardKut_>    sorry kidders...
Apr 28 20:50:46 <kidders>    sorry... i didn't mean to get us side-tracked
Apr 28 20:50:47 <jacobmp92>    RichardKut_: yeah, i suppose it's something for later
Apr 28 20:51:14 <adamtropics>    Like the idea, but suspect many people become ex-users long before becoming repeat unanswered persons!
Apr 28 20:51:26 <spyros>    kidders you are saying about a non-answered posts count per user or something like that?
Apr 28 20:51:32 <jacobmp92>    adamtropics: right on
Apr 28 20:51:35 <kidders>    yeah i guess so
Apr 28 20:51:46 <jacobmp92>    and that's what would kill the database
Apr 28 20:51:53 <spyros>    i know..
Apr 28 20:52:06 <RichardKut_>    I wonder if that functionality isn't already in the forums software?
Apr 28 20:52:31 <jacobmp92>    RichardKut_: wait a minute!
Apr 28 20:52:32 <spyros>    i am negative about coding solutions first :P i insist on human work..
Apr 28 20:52:33 <jacobmp92>    there is
Apr 28 20:52:46 <RichardKut_>    Could be updated overnight... does not need to be realtime.
Apr 28 20:52:46 <jacobmp92>    but, it can only be ran per-user
Apr 28 20:53:48 <jacobmp92>    basically, it would be the equivalent of mixing a "Find all posts by <user>" and "Only show topics with < 1 reply"
Apr 28 20:54:09 <jacobmp92>    but running on that a database of 200,000+ users isn't too feasible...
Apr 28 20:54:32 <RichardKut_>    Need an OLAP database for that.
Apr 28 20:54:49 <kidders>    hmmm :-(
Apr 28 20:54:52 <jacobmp92>    :-P
Apr 28 20:54:58 <kidders>    anyhow...
Apr 28 20:55:01 <kidders>    we should maybe give someone else a chance to ask a question hehe.
Apr 28 20:55:16 <kidders>    sorry for taking up so much time
Apr 28 20:55:32 <jacobmp92>    kidders: no problem, there is no time limit here :)
Apr 28 20:55:39 <kidders>    :)
Apr 28 20:55:46 <RichardKut_>    Your idea is good, just maybe not doable yet.
Apr 28 20:56:01 <kidders>    yeah... you're probably right.
Apr 28 20:56:04 <spyros>    well how many active member does the team has?
Apr 28 20:56:12 <jacobmp92>    let me see...
Apr 28 20:56:53 <jacobmp92>    ubuntuforums.org is slow today
Apr 28 20:57:22 <jacobmp92>    [http://ubuntuforums.org/showgroups.php](http://ubuntuforums.org/showgroups.php)
Apr 28 20:57:49 <jacobmp92>    33, by hand-counting that list :-P
Apr 28 20:57:53 <jacobmp92>    (bottom of the page)
Apr 28 20:58:33 <spyros>    got it..
Apr 28 20:58:57 <jacobmp92>    any other questions before we move onto search links/methods?
Apr 28 20:59:12 <RichardKut_>    Nope.
Apr 28 20:59:19 <ajmorris_>    none here
Apr 28 20:59:23 <spyros>    nope
Apr 28 20:59:27 <jacobmp92>    allrighty
Apr 28 20:59:28 <adamtropics>    nope
Apr 28 20:59:43 <jacobmp92>    [http://ubuntuforums.org/showthread.php?t=390283](http://ubuntuforums.org/showthread.php?t=390283)
Apr 28 20:59:53 <jacobmp92>    those are your generic search links
Apr 28 21:00:02 <jacobmp92>    which i'm sure most of you have already seen
Apr 28 21:00:27 <RichardKut_>    I hadn't, pretty cool...
Apr 28 21:00:32 <jacobmp92>    1st one makes sure posts are all older than a day, and have zero replies
Apr 28 21:00:37 <jacobmp92>    thanks :)
Apr 28 21:00:40 <spyros>    me neither :) nice..
Apr 28 21:00:54 <jacobmp92>    2nd one just finds all unanswered posts
Apr 28 21:01:03 <kidders>    yip... i use the "preferred" link a lot :-)
Apr 28 21:01:28 <jacobmp92>    and the last one, which i'm still thinking of how to revise, attempts to find bumped topics
Apr 28 21:01:44 <jacobmp92>    but it also finds bumped topics that were then answered
Apr 28 21:02:25 <jacobmp92>    but anyway, any suggestions for some new search methods? older post date times, etc?
Apr 28 21:02:31 <adamtropics>    I have a handy ff toolbar button if anyone wants it (left click link1, middle click link2)
Apr 28 21:02:44 <adamtropics>    was very bored!
Apr 28 21:02:50 <jacobmp92>    lol
Apr 28 21:02:52 <kidders>    hehe
Apr 28 21:02:58 <spd106>    I like to add forumchoice[]=136 to limit the search to the networking subforum
Apr 28 21:03:00 <RichardKut_>    Do the bumped posts only register after 24 hours too?
Apr 28 21:03:15 <jacobmp92>    RichardKut_: no, that one searches all
Apr 28 21:03:21 <RichardKut_>    ok
Apr 28 21:03:21 <jacobmp92>    but i can add one for after 24
Apr 28 21:03:23 <spyros>    well jacobmp92 if somehow we can mark the bumped posts we reply?
Apr 28 21:03:46 <kidders>    that's a smart idea...
Apr 28 21:03:46 *    mojoman (n=mojoman@c-81d1e253.023-2012-73746f2.cust.bredbandsbolaget.se) has left #ubuntuforums-unanswered ("Leaving")
Apr 28 21:03:56 <jacobmp92>    spyros: no easy way to mark them yet, the search filter might still pick them up
Apr 28 21:03:57 <RichardKut_>    I ask because I spotted a post from 7 hours ago that was bumped 12 minutes ago...
Apr 28 21:04:05 <jacobmp92>    but i'm working with the search form right now
Apr 28 21:04:06 <RichardKut_>    the poster is impatient.
Apr 28 21:04:19 <adamtropics>    and frustrated!
Apr 28 21:04:24 <jacobmp92>    RichardKut_: tell me about it. I had one that was bumped over 5 times in an hour
Apr 28 21:04:32 <RichardKut_>    Wow!!
Apr 28 21:04:41 <kidders>    i see those too. amazing!
Apr 28 21:04:58 <RichardKut_>    Some posts should be left to mellow ;)
Apr 28 21:05:02 <spyros>    does search also spot white letters?
Apr 28 21:05:06 <adamtropics>    yeah, don't make your everyday personal email address public!
Apr 28 21:05:32 <kidders>    btw, could we tweak the "bumped" search to exclude posts with a certain tag/keyword in them?
Apr 28 21:05:55 <spyros>    if yes then just add with white letters "unbumpedbyUF" :P
Apr 28 21:05:57 <jacobmp92>    kidders: i believe so
Apr 28 21:06:03 <RichardKut_>    How about all unanswered posts by category?
Apr 28 21:06:16 <adamtropics>    spyros: lol, like that!
Apr 28 21:06:22 <jacobmp92>    spyros: the problem is that we don't have mod privileges :-P
Apr 28 21:06:41 <spyros>    do we need mod privilages?
Apr 28 21:06:53 <jacobmp92>    spyros: not necessarily
Apr 28 21:06:57 <jacobmp92>    i dont even have them
Apr 28 21:07:02 <adamtropics>    no...just post to thread
Apr 28 21:07:10 <jacobmp92>    (except on the UA forum and Ohio forum)
Apr 28 21:07:13 <spyros>    when we reply to a bumped post then also add to our reply a white phrase "unbumped"
Apr 28 21:07:25 <jacobmp92>    adamtropics: right, duh!
Apr 28 21:07:29 *    jacobmp92 smacks self
Apr 28 21:07:46 <adamtropics>    spyros...don't be shy...black type would do too!
Apr 28 21:07:51 <RichardKut_>    ;)
Apr 28 21:07:58 <jacobmp92>    :-D
Apr 28 21:07:59 <spyros>    :P i know
Apr 28 21:08:25 <spyros>    then unbumped by uf-ua team :P
Apr 28 21:08:42 <adamtropics>    yeah, why not.
Apr 28 21:08:51 <jacobmp92>    that is a case where this would actually work
Apr 28 21:09:04 <adamtropics>    without coding anything!
Apr 28 21:09:05 <jacobmp92>    since a user would not want to unbump their own post themselves
Apr 28 21:09:10 <jacobmp92>    :-D
Apr 28 21:09:25 <spyros>    yeap :P
Apr 28 21:09:37 <spyros>    i thought it after proposing the white letters :P pff silly.
Apr 28 21:09:48 <RichardKut_>    How will users feel about this?
Apr 28 21:10:08 <jacobmp92>    RichardKut_: if we do it right, they'd be fine
Apr 28 21:10:09 <spyros>    and thats why i put the white letters :P
Apr 28 21:10:11 <spyros>    well
Apr 28 21:10:35 <spyros>    if we give an adequate reply and if there is nothing more to add then i dont find problem with this..
Apr 28 21:10:43 <adamtropics>    no white letters, since you are only doing it in cases where the system is somewhat abused
Apr 28 21:10:59 <RichardKut_>    So how do we proceed? What will be the text to trigger un-bumping?
Apr 28 21:11:00 <adamtropics>    people should be aware when they are asking a bit much
Apr 28 21:11:01 <jacobmp92>    im thinking something along the lines of "UA-Resolved" in the post rather than "unbumped," unbumped almost seems like it is mocking the user
Apr 28 21:11:12 <jacobmp92>    or just simply "resolved"
Apr 28 21:11:15 <RichardKut_>    agreed
Apr 28 21:11:22 <spyros>    agree :)
Apr 28 21:11:43 <RichardKut_>    Agree with the sentiment.. but which text tag?
Apr 28 21:11:45 <adamtropics>    there is a downside, in that every time you unbump a thread like this, you actually bump it!
Apr 28 21:11:51 <adamtropics>    lol
Apr 28 21:11:56 <RichardKut_>    lol
Apr 28 21:12:12 <jacobmp92>    adamtropics: not if we unbump it by answering the question in the same post :)
Apr 28 21:12:23 <RichardKut_>    Good!!
Apr 28 21:12:28 <adamtropics>    jacobmp92: I take it back, coding might help!
Apr 28 21:12:32 <jacobmp92>    lol
Apr 28 21:13:00 <spyros>    brb nature calls :P
Apr 28 21:13:07 <jacobmp92>    hehe
Apr 28 21:13:14 <kidders>    lol
Apr 28 21:13:26 <adamtropics>    coffee calls here!
Apr 28 21:13:41 <jacobmp92>    3 minute break here too :)
Apr 28 21:13:53 <RichardKut_>    Sorry.. first time in a meeting like this... when does it end?
Apr 28 21:14:02 <kidders>    (hmm... aren't you going to specify what it's for, jacob?)
Apr 28 21:14:46 <ajmorris_>    obviously not
Apr 28 21:14:47 <ajmorris_>    lol
Apr 28 21:14:53 <kidders>    haha
Apr 28 21:15:02 <spyros>    back..
Apr 28 21:15:10 <jacobmp92>    back
Apr 28 21:15:18 <kidders>    (not too much longer, richard, i'd say)
Apr 28 21:15:28 <RichardKut_>    ok, thanks
Apr 28 21:15:36 <jacobmp92>    RichardKut_: yeah, probably not too much longer
Apr 28 21:15:42 <kidders>    (but jacob is the boss.)
Apr 28 21:15:45 <RichardKut_>    kk
Apr 28 21:15:45 <adamtropics>    back
Apr 28 21:15:47 <jacobmp92>    heh
Apr 28 21:16:06 <jacobmp92>    in fact, we just have one thing left on the agenda if we are done with the search topic
Apr 28 21:16:24 <RichardKut_>    Can I ask an unrelated question quickly?
Apr 28 21:16:26 <spyros>    sum up the search topic.. ;)
Apr 28 21:16:26 <jacobmp92>    sure
Apr 28 21:16:53 <RichardKut_>    Jacob, how do you ping me like that? I am a rookie at IRC.
Apr 28 21:17:32 <jacobmp92>    RichardKut_: you mean like this? xchat beeps whenever someone says your name
Apr 28 21:17:50 <jacobmp92>    if i pinged you in another window, XChat probably did that on its own
Apr 28 21:17:51 <RichardKut_>    Cool!! Thanks.
Apr 28 21:18:24 <jacobmp92>    anywho, final topic
Apr 28 21:18:30 <jacobmp92>    Meeting times.
Apr 28 21:18:38 <jacobmp92>    Good? Not good? Better times?
Apr 28 21:18:42 <adamtropics>    now's good!
Apr 28 21:19:18 <jacobmp92>    anyone else?
Apr 28 21:19:18 <spyros>    well its 4.20 am here but i am used to sleep at 5-6am due to talk and cooperate with usa :P
Apr 28 21:19:25 <RichardKut_>    I prefer after 9:30 PM EDT, if possible.
Apr 28 21:19:44 <jacobmp92>    spyros: wow, 4:20 already?
Apr 28 21:19:57 <spyros>    greece ;)
Apr 28 21:19:58 <adamtropics>    bugger...whats EDT compared to now?
Apr 28 21:20:00 <jacobmp92>    9:30 would work for me, but i don't know about everyone else
Apr 28 21:20:06 <jacobmp92>    EDT is UTC -4
Apr 28 21:20:10 <adamtropics>    ok
Apr 28 21:20:37 <jacobmp92>    EST is -5, and that changed this year with the stupid new US laws
Apr 28 21:20:48 <jacobmp92>    its now 2 weeks earlier I believe
Apr 28 21:20:54 <adamtropics>    same day though yes?
Apr 28 21:21:03 <jacobmp92>    yeah
Apr 28 21:21:05 <RichardKut_>    OK
Apr 28 21:21:06 <spyros>    yeap..
Apr 28 21:21:13 <RichardKut_>    How often?
Apr 28 21:21:21 <adamtropics>    Australia's ok then...sunday morning!
Apr 28 21:21:26 <jacobmp92>    :)
Apr 28 21:21:41 <spyros>    greece is ok saturday night :P
Apr 28 21:21:47 <jacobmp92>    i don't know, how often do you all think we should have it?
Apr 28 21:21:47 <adamtropics>    poor thing!
Apr 28 21:22:06 <RichardKut_>    Once a month?
Apr 28 21:22:09 <adamtropics>    fortnightly seems about right to allow time for a little progress between meetings
Apr 28 21:22:24 <spyros>    RichardKut_ agree
Apr 28 21:22:24 <adamtropics>    and keep the agenda down
Apr 28 21:22:52 <RichardKut_>    Also, can we get e-mail reminders prior?
Apr 28 21:23:06 <jacobmp92>    yeah, i can go with either every 2 weeks or every month
Apr 28 21:23:07 <spyros>    crucial thing!
Apr 28 21:23:18 <adamtropics>    subscribe to the meeting thread
Apr 28 21:23:22 <jacobmp92>    RichardKut_: sure, I'll request a mailing list
Apr 28 21:23:29 <RichardKut_>    Thanks!
Apr 28 21:23:30 <jacobmp92>    adamtropics: aye, that would work also :)
Apr 28 21:23:30 <spyros>    adamtropics oke
Apr 28 21:23:35 <kidders>    just a thought jacob...
Apr 28 21:23:37 <adamtropics>    lol
Apr 28 21:23:45 <kidders>    in case someone misses a meeting...
Apr 28 21:23:51 <jacobmp92>    i'll just make a locked thread, and before each meeting post to it
Apr 28 21:24:03 <kidders>    ... someone could throw a transcript up somewhere?
Apr 28 21:24:09 <jacobmp92>    kidders: yep, i have this chat logged
Apr 28 21:24:15 <kidders>    :)
Apr 28 21:24:28 <RichardKut_>    Post it where, on launch pad?
Apr 28 21:24:45 <jacobmp92>    RichardKut_: probably the forums as a sticky
Apr 28 21:24:52 <jacobmp92>    i'll get around to it sometime tonight
Apr 28 21:24:53 <RichardKut_>    Cool
Apr 28 21:25:25 *    ajmorris__ (n=l337h4x0@220-253-0-109.VIC.netspace.net.au) has joined #ubuntuforums-unanswered
Apr 28 21:25:33 <jacobmp92>    okay, back on to frequency, do we want every two weeks or every month
Apr 28 21:25:34 <jacobmp92>    ?
Apr 28 21:25:39 *    ajmorris_ has quit (Nick collision from services.)
Apr 28 21:25:44 <spyros>    month for me
Apr 28 21:25:49 *    ajmorris__ is now known as ajmorris_
Apr 28 21:25:59 <adamtropics>    month will do fine
Apr 28 21:26:03 <jacobmp92>    i can say that every week is too much usually, we have one every week in #ubuntu-ohio and sometimes we don't have anything to talk about :-P
Apr 28 21:26:12 <jacobmp92>    all right, month it is
Apr 28 21:26:16 <adamtropics>    ah but you have fun!
Apr 28 21:26:23 <jacobmp92>    adamtropics: yes, we do :)
Apr 28 21:26:35 <ajmorris_>    are all times TBA
Apr 28 21:26:46 <jacobmp92>    can't ever have too much fun though, ubotu & locobot were watching
Apr 28 21:26:46 <ajmorris_>    ( sorry beryl crashed and killed my computer)
Apr 28 21:26:51 <RichardKut_>    How will we know when action items from a meeting have been addressed?
Apr 28 21:26:56 <adamtropics>    I think I am the only one in Cairns, would be a dull night!
Apr 28 21:27:14 <jacobmp92>    RichardKut_: as in the agenda?
Apr 28 21:27:21 <kidders>    :( that's a nasty timezone adamtropics
Apr 28 21:27:31 <jacobmp92>    ajmorris_: it should be a static time still
Apr 28 21:27:31 <RichardKut_>    ??
Apr 28 21:27:37 <ajmorris_>    ok
Apr 28 21:27:41 <ajmorris_>    is that set?
Apr 28 21:27:51 <jacobmp92>    ajmorris_: same as it is now
Apr 28 21:27:54 <adamtropics>    kidders: no, all good, although now is beach time...32 degrees and lovely day!
Apr 28 21:27:58 <ajmorris_>    adamtropics, victoria for me (GMT + 10)
Apr 28 21:28:03 <jacobmp92>    quick FYI, i'm going to post the meeting time as 00:01 to avoid the whole midnight confusion :-P
Apr 28 21:28:04 <ajmorris_>    jacobmp92, kk tks
Apr 28 21:28:11 <ajmorris_>    lol
Apr 28 21:28:15 <kidders>    adamtropics: grrr... i'm jealous!
Apr 28 21:28:28 <jacobmp92>    bah, it's storming here
Apr 28 21:28:31 <adamtropics>    ajmorris same here, now summer's over
Apr 28 21:28:39 <adamtropics>    kidders: lol
Apr 28 21:29:06 <spyros>    summer starting here but we didnt have a winter :P
Apr 28 21:29:34 <jacobmp92>    same here, not too much snow, and it was unseasonably warm
Apr 28 21:29:34 <RichardKut_>    spyros: I wish I could say the same!
Apr 28 21:29:51 <adamtropics>    spyros: sounds like our weeks, they seem to skip the weekends!
Apr 28 21:30:02 <spyros>    well when i say winter i mean 10 degrees :P
Apr 28 21:30:12 <RichardKut_>    lol
Apr 28 21:30:12 <jacobmp92>    i think all meeting stuff is in order, so i'm cutting the log --here--[/FONT]

---

### Post by jpeddicord on 2007-06-03
**Topics Covered:**
[LIST]
[*]Looking back on UAResolved, will place a poll for options
[*]Discussion of a potential offsite topic tracking system, via Firefox extension or bookmarklet[/LIST]> [FONT=Courier New]Jun 02 20:06:11 <Jacob>    woah... its 8
Jun 02 20:06:16 <Jacob>    err.. 0 utc
Jun 02 20:06:46 <Jacob>    looks like i'm late for a meeting i scheduled... ha
Jun 02 20:07:03 <kidders>    tut tut...
Jun 02 20:07:07 <kidders>    go stand in the corner
Jun 02 20:07:12 <kidders>    :P
Jun 02 20:07:21 <Jacob>    already am ;)
Jun 02 20:07:37 <kidders>    hehe
Jun 02 20:07:41 <Jacob>    anywho, no "big" topics to discuss tonight
Jun 02 20:08:07 <Jacob>    but it's been a month + 1 week since the last meeting.. so we'll check up on whats going on.
Jun 02 20:08:25 <ajmorris_>    ah
Jun 02 20:08:28 <ajmorris_>    sorry i'm late
Jun 02 20:08:43 <Jacob>    no problem ajmorris_, i just got to my laptop a minute ago :-D
Jun 02 20:09:00 <ajmorris_>    kk
Jun 02 20:09:01 <Jacob>    to start, i'm shutting off beryl because this is the 5th time it has crashed today
Jun 02 20:09:35 <Jacob>    AGH! now firefox crashes
Jun 02 20:10:19 <ajmorris_>    u using gutys dude?
Jun 02 20:10:24 <ajmorris_>    *gutsy
Jun 02 20:10:50 <Jacob>    ajmorris_: feisty, and it has only been unstable today.. i did mess with my X configuration however, i might reboot later
Jun 02 20:11:01 <ajmorris_>    kk
Jun 02 20:11:07 <Jacob>    next off: these UAresolved tags seem to be doing somewhat well
Jun 02 20:11:18 <Jacob>    80 topics tagged with them
Jun 02 20:11:44 <Jacob>    however, i'm wondering if we should keep them
Jun 02 20:12:23 <Jacob>    they are keeping "fixed" topics out of the bumped posts filter, but it still seems like a bit of a hassle at times.
Jun 02 20:12:33 <Jacob>    I even forget to put them on posts.
Jun 02 20:13:03 <ajmorris_>    i forgot we had them
Jun 02 20:13:04 <ajmorris_>    lol
Jun 02 20:13:09 <Jacob>    (so did I)
Jun 02 20:13:23 *    inkogneato has quit ("Into the great wide open...")
Jun 02 20:13:23 <kidders>    I've been lazy about it too :(
Jun 02 20:13:36 <Jacob>    I think this is something that can be polled on the forums later; on whether we shall keep them
Jun 02 20:14:39 <Jacob>    madmetal/spyros has been doing a good job of remembering it looks like, since 80% of all topics in this search were last posted by him
Jun 02 20:16:01 *    Jacob is looking thru the last meeting log to find out what was said
Jun 02 20:16:27 <spd106>    To be honest I don't like the word resolved being in there, kinda gives the wrong impression
Jun 02 20:16:44 <Jacob>    spd106: my thoughts exactly
Jun 02 20:17:05 <spd106>    UATeam would achieve the same results
Jun 02 20:17:14 <Jacob>    yeah
Jun 02 20:17:26 <spd106>    Without sounding like we had solved the problem
Jun 02 20:17:35 <kidders>    :)
Jun 02 20:17:37 <Jacob>    i actually was asked about that once
Jun 02 20:17:56 <Jacob>    (but then they saw my signature and read the answer)
Jun 02 20:18:52 <Jacob>    so our choices are: 1) keep it, 2) change it to UATeam (or similar), 3) scrap the idea
Jun 02 20:19:24 <spd106>    I like the idea of promoting our presence
Jun 02 20:19:57 <kidders>    me too. i suggest switching to "UATeam" and ...
Jun 02 20:20:11 <kidders>    ... scrapping the idea, only if it turns out not to be useful
Jun 02 20:20:17 <ajmorris_>    where is the uaresolved thing?
Jun 02 20:20:24 <ajmorris_>    i just answered a post and cant find it
Jun 02 20:20:43 <Jacob>    ajmorris_: [http://ubuntuforums.org/search.php?do=process&query=UAResolved](http://ubuntuforums.org/search.php?do=process&query=UAResolved)
Jun 02 20:21:07 <Jacob>    although it might be a few moments until the search index is updated
Jun 02 20:21:10 <ajmorris_>    Jacob, "Sorry - no matches. Please try some different terms."
Jun 02 20:21:24 <Jacob>    strange... it seems to work here
Jun 02 20:21:28 <Jacob>    try [http://ubuntuforums.org/search.php?searchid=21365822](http://ubuntuforums.org/search.php?searchid=21365822)
Jun 02 20:21:39 <Jacob>    ack - never mind
Jun 02 20:21:56 <Jacob>    try clicking on the last link on [http://ubuntuforums.org/showthread.php?t=390283](http://ubuntuforums.org/showthread.php?t=390283)
Jun 02 20:21:58 <ajmorris_>    no, but do we click a UAresolved button when resolving a post?
Jun 02 20:22:03 <Jacob>    nope
Jun 02 20:22:15 <Jacob>    you just add the text at the end
Jun 02 20:22:25 <ajmorris_>    oh, my bad
Jun 02 20:22:26 <ajmorris_>    lol
Jun 02 20:22:29 <Jacob>    :-D
Jun 02 20:23:47 <Jacob>    anyway, we'll poll this on the forums
Jun 02 20:24:46 <Jacob>    as for the suggested forum changes from last time, i can't see them happening soon
Jun 02 20:25:02 <Jacob>    (as in moving the subscribed thread box and search options)
Jun 02 20:25:28 <Jacob>    asked about the subscribed thread box, never got a response
Jun 02 20:26:06 <Jacob>    although there have been times when things have been scheduled for the next forum update and just haven't been published yet
Jun 02 20:28:29 <spd106>    I like the new "check if already posted" button, though I don't know how much it's being used
Jun 02 20:28:48 <Jacob>    i agree
Jun 02 20:29:45 <Jacob>    i think that should be a required option, especially in ABT. once they click submit, it should do a search, and ask the user if they still want to continue
Jun 02 20:30:11 <ajmorris_>    like when posting a bug in launchpad :)
Jun 02 20:30:26 <kidders>    I think so too, Jacob
Jun 02 20:30:37 <Jacob>    ajmorris_: right
Jun 02 20:31:29 <Jacob>    are all of you using firefox as your web browser?
Jun 02 20:31:36 <Jacob>    or Epiphany?
Jun 02 20:31:54 <ajmorris_>    when i don't have to use an i.e. only page, i use firefox
Jun 02 20:32:29 *    spd106 uses Firefox
Jun 02 20:32:30 <kidders>    i don't have any particular habit
Jun 02 20:33:43 <Jacob>    ack, never mind, i was thinking of something to track posts but then realized it wouldn't work out so well :-P
Jun 02 20:34:27 <kidders>    you're not going to tell us about it?
Jun 02 20:35:27 <Jacob>    well, it would have been something to the effect of a greasemonkey extension that would automatically send topics to a tracker when you reply
Jun 02 20:35:52 <Jacob>    but then i'm starting to think of privacy implications of it sending every topic link to it
Jun 02 20:36:21 <Jacob>    maybe a confirmation dialog or checkbox near the submit button
Jun 02 20:36:35 <Jacob>    let me rephrase this then, it could actually work
Jun 02 20:37:03 <Jacob>    1) You find a thread that needs answering, while already having this "extension" installed.
Jun 02 20:37:16 <Jacob>    2) You hit Reply and start writing an answer.
Jun 02 20:38:06 <Jacob>    3) The extension will add a checkbox above the Submit button to send the topic to a central location, accessible only to UA team members, where it could be tracked
Jun 02 20:38:53 <Jacob>    benefits of tracking would be the ability to ask questions between the team on a topic, and mark them as resolved/unresolved and such
Jun 02 20:39:15 <Jacob>    However this is just an idea floating around in my head
Jun 02 20:39:23 <spd106>    How about an irc bot for forum posts, like ubotu does for bug reports?
Jun 02 20:39:37 <Jacob>    spd106: yeah, and i was actually about to type that
Jun 02 20:39:48 <kidders>    Most browsers have some sort of built-in search capability that we could hijack, either.
Jun 02 20:40:05 <Jacob>    although... we need a server for an IRC bot, and my host strictly prohibits them
Jun 02 20:40:17 <Jacob>    kidders: i see what you mean, like the firefox search bar
Jun 02 20:40:32 <kidders>    Yeah... Firefox users could just drag a tab onto the search bar
Jun 02 20:40:48 <kidders>    ... Opera users could just put a "U" or something before the URL and reload it
Jun 02 20:40:55 <Jacob>    ooh, i like that idea
Jun 02 20:41:22 <Jacob>    and it seems to work when i drag a tab into the search bar (although google returns no results)
Jun 02 20:41:32 <kidders>    Yep
Jun 02 20:41:51 <kidders>    ... adding an extra "search" would be trivial for most users
Jun 02 20:42:00 <Jacob>    another option for that would be a bookmarklet, that when you click it, it takes you to a tracker
Jun 02 20:43:16 <Jacob>    kind of like the TinyURL! and reddit this buttons for toolbars
Jun 02 20:44:10 <kidders>    hmmm...
Jun 02 20:44:12 <Jacob>    i'll probably end up scripting some massive database system for this.. I script PHP when i'm bored.
Jun 02 20:44:16 <Jacob>    lol
Jun 02 20:44:30 <kidders>    The way I see it, if someone felt kind enough to create/host something that could read post IDs off URL querystrings...
Jun 02 20:44:43 <kidders>    ... there would be any number of ways it could be plugged into browsers
Jun 02 20:45:02 <kidders>    ... people could use whatever idea they thought was smartest
Jun 02 20:45:05 <Jacob>    we can give the option I suppose
Jun 02 20:45:06 <Jacob>    yeah
Jun 02 20:45:21 <kidders>    yeah
Jun 02 20:45:22 <kidders>    ...
Jun 02 20:45:29 <kidders>    from an implementation perspective...
Jun 02 20:45:45 <kidders>    the only thing that would be important would ...
Jun 02 20:46:11 <kidders>    ... be what the script liked people to send it
Jun 02 20:46:26 <kidders>    (in terms of a querystring, for instance)
Jun 02 20:47:07 <Jacob>    well.. it could either take a whole url or topic id as I'm seeing it
Jun 02 20:47:18 <kidders>    yip
Jun 02 20:47:21 <Jacob>    (thank god for regular expressions in that case)
Jun 02 20:47:24 <kidders>    lol
Jun 02 20:48:04 <Jacob>    well i'll probably make a subdomain for it tonight/tomorrow and write some sort of tracking system
Jun 02 20:49:06 <Jacob>    this is something easy enough to implement and it also takes the load off of the forum servers ;)
Jun 02 20:49:29 <kidders>    I'd be happy to help ... but I doubt you'd need it!
Jun 02 20:49:45 <Jacob>    hehe
Jun 02 20:50:27 <Jacob>    you can help draft ideas / test / code (SQL + JavaScrpt + PHP) if you want
Jun 02 20:50:34 <kidders>    sure
Jun 02 20:50:40 <Jacob>    although be warned: i don't use revision systems O.o
Jun 02 20:51:01 <kidders>    you're like me then? hehe
Jun 02 20:51:06 <Jacob>    ;)
Jun 02 20:51:34 <Jacob>    countless times have i lost many lines of code because of random server occurences
Jun 02 20:51:57 <Jacob>    forgetting to save in vim, connection drops, overwriting the wrong file...
Jun 02 20:52:01 <kidders>    nasty
Jun 02 20:52:08 <Jacob>    but i have survived still....
Jun 02 20:52:23 <Jacob>    maybe i'll use Baazar on it soon
Jun 02 20:52:32 <Jacob>    but not yet ;)
Jun 02 20:54:24 <Jacob>    I have nothing else to say for this meeting, anybody have anything?
Jun 02 20:54:55 <ajmorris_>    none here
Jun 02 20:54:58 <spd106>    nope
Jun 02 20:55:10 *    kidders has quit (Read error: 113 (No route to host))
Jun 02 20:55:19 <Jacob>    i'd take that as a no :-P
Jun 02 20:55:23 <ajmorris_>    lol[/FONT]

---

### Post by jpeddicord on 2007-06-25
Short meeting, just discussing some ways of posting and having fun with the tracker and bot.
> [FONT=Courier New]Jun 23 20:00:04 <Jacob>    Welcome to the 3rd (?) meeting. Yay...
Jun 23 20:00:36 <Jacob>    Nothing on schedule to talk about tonight other than the new system kidders wrote and ajmorris_ styled up
Jun 23 20:00:42 <ajmorris_>    agenda...?
Jun 23 20:00:47 <Jacob>    ^
Jun 23 20:01:21 <Jacob>    so basically, we're killing off uaresolved tagging as of the last meeting, right?
Jun 23 20:01:42 <ajmorris_>    that was my understanding
Jun 23 20:01:47 <Jacob>    ok, just making sure
Jun 23 20:01:55 <madmetal_spyros>    ok i missed last meeting :(
Jun 23 20:02:07 <kidders>    bad boy
Jun 23 20:02:07 <Jacob>    hehe no prob madmetal_spyros 
Jun 23 20:02:20 <Jacob>    actually you were the only one remembering to put the tag in the posts lol
Jun 23 20:02:27 <madmetal_spyros>    yeap :P
Jun 23 20:02:34 <reclusivemonkey>    I did pop one in the other day...
Jun 23 20:02:34 <madmetal_spyros>    cause i was up to the idea :P
Jun 23 20:02:39 <ajmorris_>    LOL
Jun 23 20:02:44 <Jacob>    hehe
Jun 23 20:02:52 <Jacob>    yeah reclusivemonkey i saw you in here once
Jun 23 20:02:54 <madmetal_spyros>    so i will continue :P pfff
Jun 23 20:02:57 <Jacob>    lol
Jun 23 20:04:00 <Jacob>    madmetal_spyros: you still need a UA tracker account.. have you seen the system yet?
Jun 23 20:04:06 <Jacob>    [http://ua.codechunk.net](http://ua.codechunk.net)
Jun 23 20:04:20 <reclusivemonkey>    lol I meant a "uaresolved"... I agree its probably better to track "our" resolved threads outside the forums. Its probably only of interest to ourselves...
Jun 23 20:04:22 <madmetal_spyros>    yeap i just saw it ;)
Jun 23 20:04:33 <Jacob>    i agree reclusivemonkey ;)
Jun 23 20:04:58 <Jacob>    lol and once again kidders beat me to the chase
Jun 23 20:05:03 <madmetal_spyros>    Jacob kidders ajmorris_  i need an account :P
Jun 23 20:05:05 <kidders>    i did?
Jun 23 20:05:08 <kidders>    what did i do?!
Jun 23 20:05:10 <Jacob>    err.. hmm
Jun 23 20:05:12 <Jacob>    wait
Jun 23 20:05:28 <Jacob>    nvm.. that was the queue cron job speaking
Jun 23 20:05:49 <Jacob>    an error popped up when i was adding a user, from UF saying that there is a 15-second search barrier
Jun 23 20:05:51 <madmetal_spyros>    brb
Jun 23 20:05:52 <reclusivemonkey>    I think another idea for the website is to put a list of "official" HOWTOs that we can point people to for the more obvious answers, like [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
Jun 23 20:05:53 <ajmorris_>    and don't for get to add the site to an rss live bookmark :)
Jun 23 20:06:09 <kidders>    Jacob, oh sorry... my fault
Jun 23 20:06:11 <Jacob>    ah ajmorris_ i forgot about that
Jun 23 20:06:16 <Jacob>    nah, no prob
Jun 23 20:06:41 <Jacob>    madmetal_spyros: i'm /msg'ing you your username and password
Jun 23 20:07:43 <kidders>    reclusivemonkey, Jacob & I were chatting about something related to that
Jun 23 20:07:48 <kidders>    ... i think it's a good idea
Jun 23 20:07:51 <kidders>    ... personally
Jun 23 20:07:52 <Jacob>    yeah
Jun 23 20:08:17 <ajmorris_>    hmm....
Jun 23 20:08:19 <Jacob>    i wasn't able to find the Beginners team responses.... i thought they were there, but apparently they aren't
Jun 23 20:08:39 <ajmorris_>    that is what the UF-BT is doing though... they are making wikis for more obvious answers
Jun 23 20:08:39 <madmetal_spyros>    back
Jun 23 20:08:41 <reclusivemonkey>    encouraging people to use the existing guides where appropriate can only be a good thing
Jun 23 20:08:51 <kidders>    yeah
Jun 23 20:08:51 <Jacob>    yeah
Jun 23 20:09:02 <kidders>    if we were to compile ourselves a list of good urls...
Jun 23 20:09:17 <kidders>    ... we could have the uatracker help us insert them into posts
Jun 23 20:09:24 <reclusivemonkey>    ajmorris_: yeah, I don't think the things that slip through will be *as* obvious
Jun 23 20:09:41 <ajmorris_>    kk
Jun 23 20:10:04 <Jacob>    kidders: the problem with having the tracking system insert them is account access for one thing
Jun 23 20:10:15 <reclusivemonkey>    once we have some results from the tracker, we can even spot things that might be asked frequently and add them to the appropriate wiki(s)
Jun 23 20:10:39 <Jacob>    i think we just need a page with them on it or a script (greasemonkey anyone?) to insert them
Jun 23 20:10:45 <kidders>    Jacob, i was thinking of something much more low-tech...
Jun 23 20:10:53 <kidders>    ... that would only be semi-automated
Jun 23 20:10:56 <Jacob>    ah
Jun 23 20:11:04 <kidders>    losing the personal touch to posting...
Jun 23 20:11:07 <kidders>    ... would be bad
Jun 23 20:11:21 <Jacob>    lol
Jun 23 20:11:53 <kidders>    but at the same time, it would be nice to be able to select howto URLs from lists, rather than having to search for them & type them manually?
Jun 23 20:12:04 <Jacob>    yeah i agree with that
Jun 23 20:12:07 <kidders>    reclusivemonkey, yep :D
Jun 23 20:12:26 <Jacob>    i think we could have a text file on the ua site with canned responses / links
Jun 23 20:12:38 <Jacob>    and then use a firefox greasemonkey script to fetch them on the reply form
Jun 23 20:12:47 <kidders>    Jacob, perhaps a firefox plugin that looks like a live bookmark...
Jun 23 20:12:47 <Jacob>    and put them as a select menu or something
Jun 23 20:12:53 <Jacob>    yeah
Jun 23 20:12:59 <Jacob>    something along those lines
Jun 23 20:14:02 <kidders>    i've been working on a uateam toolbar plugin...
Jun 23 20:14:14 <ajmorris_>    ooh :)
Jun 23 20:14:19 <kidders>    ...with a collection of gizmos in it that might be useful for the team
Jun 23 20:14:27 <kidders>    ...
Jun 23 20:14:34 <ajmorris_>    good idea kidders :)
Jun 23 20:14:39 <Jacob>    dang kidders you are doing everything ;)
Jun 23 20:14:42 <kidders>    hehe :)
Jun 23 20:14:44 <kidders>    sorry
Jun 23 20:14:53 <Jacob>    nothin to be sorry 'bout
Jun 23 20:15:02 <kidders>    heh
Jun 23 20:15:07 <kidders>    it just strikes me that ...
Jun 23 20:15:16 <kidders>    perhaps an embedded drop-down list that would let ...
Jun 23 20:15:30 <kidders>    people select good howtos...
Jun 23 20:15:42 <kidders>    and auto-insert the url into a post...
Jun 23 20:15:46 <kidders>    would be a nice addition
Jun 23 20:16:00 <Jacob>    yeah
Jun 23 20:16:00 *    kidders wonders if that made any sense
Jun 23 20:16:06 <Jacob>    i get ya
Jun 23 20:16:07 <madmetal_spyros>    yeap
Jun 23 20:16:17 <reclusivemonkey>    kidders: yep, that would certainly be helpful
Jun 23 20:16:18 <Jacob>    and greasemonkey scripts are able to accomplish that
Jun 23 20:16:24 <kidders>    :)
Jun 23 20:16:55 <kidders>    Jacob ... it's really only a matter of a few lines of javascript
Jun 23 20:17:00 <kidders>    ... thankfully
Jun 23 20:17:01 <kidders>    hehe
Jun 23 20:17:09 <Jacob>    the scripts are all javascript... all that is needed is a little JS + DOM + AJAX (to fetch the canned list)
Jun 23 20:17:11 <Jacob>    yeah
Jun 23 20:17:24 <kidders>    yup
Jun 23 20:18:03 *    ajmorris_ feels out of place..... the only code i know ATM is HTML and CSS
Jun 23 20:18:04 <ajmorris_>    lol
Jun 23 20:18:09 <Jacob>    hehe
Jun 23 20:18:25 <ajmorris_>    and soon php....
Jun 23 20:18:25 <Jacob>    python python python python python python python python python 
Jun 23 20:18:30 <Jacob>    :-D
Jun 23 20:18:33 <ajmorris_>    lol....
Jun 23 20:18:38 <kidders>    snack snack snack snack snack
Jun 23 20:18:46 <Jacob>    yum yum yum yum yum 
Jun 23 20:18:47 <ajmorris_>    will find a tutorial on w3c if i can for python so i can learn it
Jun 23 20:18:53 <ajmorris_>    LOL
Jun 23 20:19:04 <Jacob>    python isn't on the w3c ;)
Jun 23 20:19:05 <ajmorris_>    uab snack snack snack snack
Jun 23 20:19:06 <uab>    huh?
Jun 23 20:19:09 <madmetal_spyros>    ajmorris_ i am far away than you are :P
Jun 23 20:19:12 <Jacob>    [http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)
Jun 23 20:19:15 <madmetal_spyros>    uab code
Jun 23 20:19:16 <uab>    what?
Jun 23 20:19:19 <ajmorris_>    lol
Jun 23 20:19:22 <Jacob>    hehe
Jun 23 20:19:25 <ajmorris_>    thanks jacob
Jun 23 20:19:45 <ajmorris_>    what sort of stuff is made in python?
Jun 23 20:19:57 <kidders>    absolutely everything
Jun 23 20:19:57 <madmetal_spyros>    deluge
Jun 23 20:19:58 <Jacob>    everything, from web apps to applications
Jun 23 20:20:00 <madmetal_spyros>    :P
Jun 23 20:20:01 <kidders>    blender
Jun 23 20:20:05 <Jacob>    tons of ubuntu apps are in python
Jun 23 20:20:07 <kidders>    gimp
Jun 23 20:20:14 <ajmorris_>    wow.....
Jun 23 20:20:17 <ajmorris_>    this is awesome
Jun 23 20:20:21 <Jacob>    heck, ubuntu.com used to be all python before they switched to Drupal
Jun 23 20:20:21 <kidders>    scientology
Jun 23 20:20:24 <Jacob>    lol
Jun 23 20:20:25 <reclusivemonkey>    kidders: gimp is in python?
Jun 23 20:20:26 <kidders>    (lol)
Jun 23 20:20:32 *    ajmorris_ bookmarks the page to learn python after the meeting
Jun 23 20:20:36 <kidders>    reclusivemonkey ... its plugins are
Jun 23 20:20:38 <Jacob>    gimp is in C i think... but it has Python extensions
Jun 23 20:20:41 <reclusivemonkey>    ah
Jun 23 20:20:51 <Jacob>    ugh I hate C and C++
Jun 23 20:20:56 <kidders>    hehe
Jun 23 20:21:03 <kidders>    they're a necessary evil
Jun 23 20:21:04 <Jacob>    C lets you shoot off your foot
Jun 23 20:21:13 <madmetal_spyros>    i bookmarked the page to learn python after summer :P
Jun 23 20:21:14 <reclusivemonkey>    I know a little HTML/CSS/XML/XSL/VBA/bash scripting
Jun 23 20:21:14 <kidders>    i like that in a language!
Jun 23 20:21:22 <Jacob>    C++ makes it harder, but if you do manage to it will take off your whole leg
Jun 23 20:21:31 <kidders>    roflmao
Jun 23 20:21:39 *    kidders ponders
Jun 23 20:21:48 <kidders>    ... so that's why i've been finding it so hard to walk lately
Jun 23 20:21:51 <Jacob>    lol
Jun 23 20:22:36 <Jacob>    ooh... fresh bait in the ua join queue
Jun 23 20:22:47 <kidders>    ?
Jun 23 20:22:49 <kidders>    lol
Jun 23 20:22:52 <Jacob>    lol
Jun 23 20:23:03 <Jacob>    someone applied to the group
Jun 23 20:23:03 <ajmorris_>    how many members we at now?
Jun 23 20:23:20 <Jacob>    idk
Jun 23 20:23:25 <kidders>    let's all be sure to tell the poor soul what Jacob thinks of him, eh?
Jun 23 20:23:26 <kidders>    hehe
Jun 23 20:23:28 <Jacob>    never really counted :-D
Jun 23 20:23:31 <Jacob>    lol
Jun 23 20:23:49 <Jacob>    [http://ubuntuforums.org/showgroups.php](http://ubuntuforums.org/showgroups.php)
Jun 23 20:23:58 <Jacob>    we're at the bottom, with the exception of ubuntu-geek
Jun 23 20:24:13 <kidders>    it's biiiiiig!
Jun 23 20:24:19 <kidders>    (our list)
Jun 23 20:24:24 <Jacob>    hehe, it is
Jun 23 20:24:29 <Jacob>    and one is about to be added
Jun 23 20:25:23 <ajmorris_>    37 +1 for the new person :)
Jun 23 20:25:27 <Jacob>    'ere he is: [http://ubuntuforums.org/member.php?u=35362](http://ubuntuforums.org/member.php?u=35362)
Jun 23 20:25:41 <kidders>    yeeks
Jun 23 20:25:54 <kidders>    a bloody cat!
Jun 23 20:25:57 <Jacob>    lol
Jun 23 20:25:58 <kidders>    hehe
Jun 23 20:26:07 <reclusivemonkey>    we should see if we could keep a count of the unanswered posts and see if we can track the %age over time...
Jun 23 20:26:07 *    kidders doesn't much care for cats
Jun 23 20:26:29 <Jacob>    reclusivemonkey: it's hard to count them though... i think the search caps off at 25 pages
Jun 23 20:26:31 <kidders>    reclusivemonkey, the %age that go unanswered?
Jun 23 20:26:51 <kidders>    my "unlucky" user finder effectively does that
Jun 23 20:26:51 <kidders>    ...
Jun 23 20:26:53 <kidders>    sort of
Jun 23 20:26:57 <Jacob>    yeah
Jun 23 20:26:58 <reclusivemonkey>    Jacob: Ah, that would explain the constant 250!
Jun 23 20:27:01 <Jacob>    hehe
Jun 23 20:27:08 <Jacob>    was it 250 pages?
Jun 23 20:27:16 <kidders>    (interesting idea, reclusivemonkey)
Jun 23 20:27:41 <reclusivemonkey>    It would be nice to see it going down =]
Jun 23 20:27:45 <kidders>    sure would
Jun 23 20:27:55 <Jacob>    yeah
Jun 23 20:28:01 <reclusivemonkey>    250 posts I think...
Jun 23 20:28:02 <kidders>    that'd be the *real* measure of our success
Jun 23 20:28:30 <kidders>    reclusivemonkey, i'll add a graph of the numbers of unanswered posts to the ua site
Jun 23 20:28:49 <Jacob>    yeah 250 results
Jun 23 20:28:50 <reclusivemonkey>    kidders: That would be great!
Jun 23 20:29:03 <kidders>    :D
Jun 23 20:29:06 <Jacob>    the rest of them are thrown into the void of lost searches
Jun 23 20:29:15 <kidders>    yeah :(
Jun 23 20:29:17 <Jacob>    kidders, awesome
Jun 23 20:29:30 <reclusivemonkey>    If we could break it down into unanswered posts per forum / total posts per forum that would be more accurate
Jun 23 20:29:32 <Jacob>    (about the graphs, not the posts)
Jun 23 20:29:38 <Jacob>    yeah
Jun 23 20:29:40 <kidders>    lol
Jun 23 20:29:44 <kidders>    yep reclusivemonkey
Jun 23 20:29:59 <kidders>    (my gizmo stores enough data locally to do that, i think)
Jun 23 20:29:59 <Jacob>    we'll see if we can make u-g forefit the data on that ;)
Jun 23 20:30:18 <Jacob>    or if kidders method works anyway
Jun 23 20:30:26 <kidders>    i don't mind
Jun 23 20:30:34 <kidders>    :P
Jun 23 20:30:46 <reclusivemonkey>    kidders seems like the man who can =]
Jun 23 20:30:51 <Jacob>    hehe
Jun 23 20:30:52 <kidders>    lol not really
Jun 23 20:33:30 <kidders>    erm... am i still connected?
Jun 23 20:33:39 <ajmorris_>    yep
Jun 23 20:33:45 <reclusivemonkey>    ask uab ;-)
Jun 23 20:33:46 <uab>    quit rambling, reclusivemonkey
Jun 23 20:33:49 <kidders>    hehe kewl... everything went so quiet![/FONT]

---

