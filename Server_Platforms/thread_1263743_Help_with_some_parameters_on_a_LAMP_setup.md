---
title: "Help with some parameters on a LAMP setup"
date: 2009-09-11
forum: Server Platforms
---

### Post by RagingAardvark on 2009-09-11
Hi folks,
I'm trying to set up some background processes and am working (blindly) through a few steps that I have found ;

1) The exec() function in PHP needs to be enabled
2) Your web users need to be able to run PHP server commands using the exec() function
3) Your web users must be able to send jobs to the background (&>/dev/null &)

I think that I've sorted the 1) by setting disable_functions and safe_mode to Off in php.ini

The other two though I'm really struggling to understand. 

Please could someone shed some light on what the two steps mean?

Many thanks.

KJ

---

### Post by Sporkman on 2009-09-11
> **RagingAardvark said:**
> Hi folks,
I'm trying to set up some background processes and am working (blindly) through a few steps that I have found ;

1) The exec() function in PHP needs to be enabled
2) Your web users need to be able to run PHP server commands using the exec() function
3) Your web users must be able to send jobs to the background (&>/dev/null &)

I think that I've sorted the 1) by setting disable_functions and safe_mode to Off in php.ini

The other two though I'm really struggling to understand. 

Please could someone shed some light on what the two steps mean?

Many thanks.

KJ

I hope these are trusted users from behind a firewall. :)

So do you want the user to type into a field on a webpage a console command, click a submit button, then have that command run on the server in the background (without the page reload waiting for the command completion)?

---

### Post by RagingAardvark on 2009-09-12
The users are all behind a firewall - so as trusted as they can be!

The idea is they can upload a video and then mencoder will automatically run in the background to convert the video to .flv

I've got it working with a cron job and ffmpeg, but the mencoder solution is a lot more elegant.

---

### Post by Sporkman on 2009-09-12
> **RagingAardvark said:**
> The users are all behind a firewall - so as trusted as they can be!

The idea is they can upload a video and then mencoder will automatically run in the background to convert the video to .flv

I've got it working with a cron job and ffmpeg, but the mencoder solution is a lot more elegant.

Then you can provide them a straightforward command-line interface, by taking a command from an html input field & running it through the passthru() fcn, which executes the command on the command line & prints out the output. Or you can rig up something fancier if they're not completely command-line savvy or if you want to have more control over how jobs get submitted, etc.

---

