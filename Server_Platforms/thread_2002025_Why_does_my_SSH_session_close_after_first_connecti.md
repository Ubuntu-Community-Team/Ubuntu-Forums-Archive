---
title: "Why does my SSH session close after first connection?"
date: 2012-06-12
forum: Server Platforms
---

### Post by Maheriano on 2012-06-12
I wrote an Android application which connects to my desktop on launch via SSH (JSCH library). Then when you press one of the buttons it sends a command to be executed on the host machine. I press the first button, command gets executed successfully. But when I press another button and debug the code, the channel on the session is closed. Somehow the command still executes successfully but hitting a third button is completely unresponsive because the channel is totally closed and doesn't allow any more commands to be sent through.

To make sure it's not my code I set it up to send multiple commands on a single push of a button and again only the first 2 got executed successfully. None of the subsequent commands worked.

Here's some of my code in case you want to see it anyway but I'm sure it's not that. I'm almost positive there is a setting on the host to limit the number of connections via an SSH session, is this possible? Where would I find this? It's not any sort of high tech server, it's just your regular desktop computer with Ubuntu 12.04 and SSH installed on it. No proxy, no fancy networking. And I forwarded my switch to my desktop on port 22 so I can access it outside the network. Any ideas?

This is the method to connect to my host computer (my desktop):

```
	public ChannelExec connect(String username, String password, String hostname, int port) throws Exception
	{
		JSch jsch = new JSch();
		
		
		session = jsch.getSession(username, hostname, 22);
		
		session.setPassword(password);
		
		// Avoid asking for key confirmation
		Properties prop = new Properties();
		prop.put("StrictHostKeyChecking", "no");
		session.setConfig(prop);
		
		session.connect();
		
		// SSH Channel
//		ChannelExec channelssh = null;
		channelssh = (ChannelExec)session.openChannel("exec");

		ByteArrayOutputStream baos = new ByteArrayOutputStream();
		channelssh.setOutputStream(baos);
		
		return channelssh;
	}
```

This is the code called to execute the passed string as a command on the host machine:

```
	public void send(String command) throws Exception
	{
		// Execute command
		channelssh.setCommand(command);
		channelssh.connect();
		channelssh.disconnect();
	}
```

This is what is run when the application is launched and also a button listener which is run when the button is pressed. It runs a program called Heyu which is a home automation program, I'm telling it to turn on my bathroom light which is addressed at a12. It's not my home automation system because I built it 3 years ago and it's been bulletproof ever since. Plus I can SSH into the box from my laptop and everything works perfectly for as many commands as I want to send.

```
      	  final InitTask _initTask = new InitTask();
   	      _initTask.execute("");

         
         final Button button1_on = (Button) findViewById(R.id.button1_on);
         button1_on.setOnClickListener(new View.OnClickListener()
         {
             public void onClick(View v)
             {
				  try {_initTask.send("heyu on a12");}
				  catch (Exception e) {e.printStackTrace();}
	       	 }
         });
```

---

### Post by Maheriano on 2012-06-12
I feel like every time I post the question on a forum I figure it out myself. Here is what I did to fix it, I had to recreate the channel object and destroy it every time I used it. I couldn't seem to use the same channel more than once.

```

	public void send(String command) throws Exception
	{
		ChannelExec channelssh = (ChannelExec)session.openChannel("exec");

		ByteArrayOutputStream baos = new ByteArrayOutputStream();
		channelssh.setOutputStream(baos);
		
		// Execute command
		channelssh.setCommand(command);
		channelssh.connect();
		channelssh.disconnect();
		channelssh = null;
	}

```

---

