Bitlbee Discord via Docker Container 

This project uses bitlbee with bitlbee-discord plugin (see: https://github.com/sm00th/bitlbee-discord)
Docker image is based on debian stretch.

You may ask, why docker?
Because it will just work on all distros without messing around with packages, dependencies and manual building. 

Anyway, after running this containter you will be able to conenct bo bitlbee from your favorite IRC client. Enjoy. 

Quick how to use:
Run `setup.sh` or follow these steps:
1. Run container like this
```
docker run --restart on-failure -d -p 127.0.0.1:<bitlbee_port_on_your_host>:6667 -v your/bitlbee/settings/dir/on/host:/var/lib/bitlbee bitlbee-discord
```
you can also use -u flag (make sure that directory for your bitlbee settings exists!), for example: 
```
docker run --restart on-failure -d -u $(id -u $USER):$(id -g $USER) -p 127.0.0.1:<bitlbee_port_on_your_host>:6667 -v your/bitlbee/settings/dir/on/host:/var/lib/bitlbee bitlbee-discord
```
2. After running this container just connect to it from your IRC client, for example:
```
/connect localhost 16667
```
3. Set up bitlbee to use discord by swtiching to "&bitlbee" window:
```
register <bitlbee_password>
account add discord <your@discord.mail> <discord_pass>
account discord on
```
And you are connected to Discord!

Use `chat list discord` to list available rooms, then execute these commands to join one of them:

```
  chat add discord !1 #mydiscordchannel
  chan #mydiscordchannel set auto_join true
  /join #mydiscordchannel
```
To store your settings use `save` command. To login into bitlbee after connectiong use `identify <bitlbee_password>` command.  

If you want to see offline people on discord channels run
```
account discord off
account discord set never_offline on
account discord on
```
If you want to see everyone from your channels in bitlbee window use this"  
```
account discord friendship_mode off
```

Further reading: bitlbee offical docs, bitlbee-dicord docs.
