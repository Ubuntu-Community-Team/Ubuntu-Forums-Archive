---
title: "[C]Fifo vs Client/Server"
date: 2014-07-30
forum: Ubuntu Application Development
---

### Post by csimone2 on 2014-07-30
Hi everyone,
I'm new here... I want to premise I don't want the solution to my problem but I need to understand which is difference between a client/server program and a FIFO reader/writer program... I explain better... 

I have to do a project for an exam. The purpose of the project is "define script Bash and C programs to correct automatically the examination tasks."

The professor ask to me to write some Bash scripts to take the examination tasks, check them and, for each task, write the scores **on a file**. Everything is clear until now.
[COLOR=#101010][FONT=Ubuntu][/FONT][/COLOR]
Then the professor ask 4 C program and I do not understand anything anymore. I translate in English exactly what is written in the project specification:
> [B]
fifo_reader 
[/B]It's a C client that read the content of a FIFO and print it on the stdout
Take as parameter (as argument from command line) the Fifo's name

[B]fifo_writer
[/B]It's a C client that write the content of the stdin in a FIFO
Take as parameter (as argument from command line) the Fifo's name

**network_server_echo**
It's a C server that listen to a net port (TCP or UDP) (number of the port and backlog value passed as argument from command line) and:
  1. read the strings on the input stream 
  2. write the string that has been read on the correspondent output stream 

**network_client_echo**
It's the client version of the network_server_echo

Here what i do not understand: 
A fifo writer/reader is not like a client/server application with socket? So, the professor is asking us the same thing in two different ways? But when the professor talk about fifo reader/writer, he define both them **client... **Perhaps I have not understood what the professor is really asking us....Can anyone help me plz?

Thanx

---

