# Themer wordpress event
This event is a part of the [devbot project](https://github.com/sharovik/devbot) which can be used for automation of your daily development routine.

## Example of output
![Demo file processing](documentation/images/demo-file-processing.gif)

## Installation guide

### Clone into devbot project
```
git clone git@github.com:sharovik/themer-wordpress-event.git events/themerwordpress
```

### Install it into your devbot project
1. clone this repository into `events/` folder of your devbot project. Please make sure to use `themerwordpress` folder name for this event 
2. add into imports path to this event in `defined-events.go` file
``` 
import "github.com/sharovik/devbot/events/themerwordpress"
```
2. add this event into `defined-events.go` file to the defined events map object
``` 
DefinedEvents.Events[themerwordpress.EventName] = themerwordpress.Event
```

### Database installation
To install it please run 
``` 
make build-installation-script && scripts/install/run --event_alias=themer_wordpress_event
```

### PHP installation
You server requires php version of 7.1+ with php-dom module. `It is only required if you will use the wordpress template generation event.`
For ubuntu
```
sudo apt install php php-dom
```
Or for brew
```
brew install php
```
Or for centos
```
yum install php php-xml
```

## How to use
1. Prepare a `*.twig` template and compress it in a `*.zip` file ([here you can find the example of template](https://github.com/sharovik/themer)) 
2. Open PM of the bot, channel where this bot was added or tag bot-user during the attachment send
3. In attachment popup please write in comment field `process` word and send the attachment
4. After bot received your attachment you will see the answer
 >Please, wait a bit. I have to process this file
 
 Up to 4 seconds will take to process the template
5. After template was processed you will receive in answer new archive where you will find `html preview of your template` and WordPress template
