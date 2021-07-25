# Streamer Song List overlays

A simple overlay for displaying your current queue on streamersonglist.com.


## Initial setup

Download the ZIP file and extract it somewhere on your computer, for example, **C:\streamoverlays**.

Hey Mike, I'm assuming that you haven't been on GitHub before. As long as you stay on this page (where it says `/tree/toehider` in the address bar) you're viewing the code that's tailored for you. It's called the `toehider branch`.If you don't see this paragraph any more, you'll be on a different branch, viewing code that you can't simply download and start using. Just go to the original link again to return here.

## Testing

If you would like to test if it's working properly, you can open the ```queue.html``` file in your browser. Usually you can just double-click this from Windows Explorer to open it in a browser.

You should see "queue is empty". If this is the case, you can add songs to your queue using streamersonglist.com and make sure that they appear. You will need to wait up to 10 seconds to see the changes show up.

## Streaming setup

Add a new Browser Source to your overlays. This should be at a width of 480, and a height to suit. If you are planning to have a long queue, you might want a bigger height. 480 is a good default if you're not sure.

Pick **use local file** and then find the ```queue.html``` file from your download, such as **C:\streamoverlays\queue.html**.

When you save, you should see the queue (or lack of queue) show up in the overlay immediately.

## Known issues

Because we need to make two different API requests sometimes, not all the data will load in, when the page (overlay) first loads. It will update properly once it refreshes for the first time.

For example, if you have a maximum number of requests, it will always show as 0 when the overlay first loads, and will update after ten seconds.

## Settings

You can customise a lot of settings by editing the ```const``` values at the top of ```lib/streamersonglist.js```. Just open it in your favourite text editor and refer to the settings below for an explanation.

### apiUrl

The URL where the streamersonglist.com API is found. You will not need to edit this!

### streamerName

Your name on Twitch, in lower case. This should match the name you're using on streamersonglist.com as well, which is normally automatic when you sign up.

For example, if your name on Twitch is "My_Cool_Name", you would use "my_cool_name" (lower case).

On this branch, I've already set it to "toehider".

### streamerId

Not currently used.

### allCaps

If this is ```true```, it will cause the queue to be shown in capital letters all the time. If this is ```false```, a mix of upper case and lower case will be used.

### maxQueueItems

The maximum number of items that will be shown in the queue. For example, if you set this to ```3```, only the first three items in the queue will appear. See **showMore** if you want to let viewers know that there are more than your maximum number of items in the queue.

Note that setting this to ```0``` will not cause an unlimited number of items to be shown. If you want an unlimited number to be shown, set this to ```999``` or another really high value. This is not recommended, because eventually the bottom of the queue will go off the screen!

### showMore

If ```true```, a "+X more in queue" message will appear at the bottom of the queue when there's more items in the queue than **maxQueueItems**. Set this to ```false``` if you don't want this to show at the bottom.

### showSongLimit

If set to something other than ```no```, will show the request limit current configured in Streamer Song List.
  
 There are two possible values you could use here:
 - ```maximum``` will show the total number of requests allowed for this stream, as set by your "Song Limit" in the Streamer Song List queue settings.
 - ```remaining``` will show the number of requests that are remaining, which is the maximum minus the number that have already been played.

### songLimitMessage

If showSongLimit is ```remaining```, this controls the message that will appear on the screen. The ```#``` will be replaced by the remaining number of requests, and plurals (request/requests) will be handled automatically.