# Mk.1
Day trading bot
from flask import Flask, jsonify, request
from bot import TradingBot

app = Flask(__name__)
bot = TradingBot()

@app.route('/start', methods=['POST'])
def start():
    bot.start()
    return jsonify({"status": "Bot started"})

@app.route('/stop', methods=['POST'])
def stop():
    bot.stop()
    return jsonify({"status": "Bot stopped"})

@app.route('/status', methods=['GET'])
def status():
    return jsonify({"status": bot.status()})

if __name__ == '__main__':
    app.run(debug=True)
