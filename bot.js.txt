const mineflayer = require('mineflayer')

const bot = mineflayer.createBot({
  host: 'souptik.aternos.me', // put your aternos IP
  port: 44529,
  username: 'AFK_Bot',
  version: false
})

bot.on('spawn', () => {
  console.log('Bot joined the server!')

  // jump every 10 seconds
  setInterval(() => {
    bot.setControlState('jump', true)

    setTimeout(() => {
      bot.setControlState('jump', false)
    }, 500)

  }, 10000)
})

bot.on('end', () => {
  console.log('Bot disconnected')
})

bot.on('kicked', (reason) => {
  console.log('Kicked:', reason)
})

bot.on('error', (err) => {
  console.log('Error:', err)
})