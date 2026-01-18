# Get Mailbox audio file off NuPoint

First get the Mailbox of the call flow e.g. Mailbox 3355
On the MSL go the directory where the Call Flows are configured

`cd /usr/vm/val5/CallFlows`

Find your mailbox config and view the contents using your preferred editor. e.g.

`vim mbox_3355.xml`

Look in the file for the nodeID your looking for and under that line will be the messageID
In my example I had

`<messageID>32020</messageID>`

This number is in decimal format but the audio files are named in hex.
Convert the number to hex i.e 32020 = 00007d14
Go to the directory where the audio files are stored.

`cd /usr/vm/audio/store`

Search for your audio files (named in hex)

`find -iname "*7d14"`

This will show you what directory the audio file is stored in. Mine was `./0/125/00007d14`
Use your favourite way of getting files off the server. I use WinSCP.

I believe the file is in some raw format. I use Audacity to convert it by importing raw data, U-Law, No endianess, 1 Channel (Mono), 8000Hz
You can then export it whatever format you like.
