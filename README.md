# Analysis of an avergae python token grabber

The following exe is just the average pasted python info stealer that's usually disguised as a game or free cheat for a game.

### Reversal For FLVS
First, I confirmed that the exe was a token grabber to begin with, so I dropped it into [Hatching Triage](https://tria.ge/) so
I could run it inside of a sandbox.

<img src="https://cdn.discordapp.com/attachments/829325901984563211/1100420088626159636/image.png">
After running it inside of the sandbox, the results pointed to it most likely being a token grabber, so I dropped it into Detect-It-Easy
to find out what the application was made in.


<img src="https://cdn.discordapp.com/attachments/829325901984563211/1100420777964212224/image.png">
The exe seems to be just a python file compiled into an exe using pyinstaller lol.

So I dumped the exe using pydumpck (great tool for this type of thing)
Upon snooping around the main.py file I found out that they used a [public method](https://raw.githubusercontent.com/KingKrex69/Discord-Injection/main/injection.js
) for injecting malicious code into user's discord token

Looking further into the dump I found a config file which seemed to be encrypted using b64
<img src="https://cdn.discordapp.com/attachments/829325901984563211/1100422327415607477/image.png">

I made a very simple script to decode and decompress the encrypted strings in visual studio 
<img src="https://cdn.discordapp.com/attachments/829325901984563211/1100423146424778862/image.png">

Upon decoding, it turned out to be a discord webhook, which was most likely where the stolen information was being sent to
<img src="https://cdn.discordapp.com/attachments/829325901984563211/1100423528479731822/image.png">

So, all I had to do was destroy the webhook using https://webhooks.scam.gay/ to prevent other individuals from being infected

In conclusion, please don't run every file you get sent, even if said file is sent by a friend, and always run an untrusted application in a controlled
environment before running it on your main device.
