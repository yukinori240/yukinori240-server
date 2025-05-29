# yukinori240-server
import requests

API_KEY = 'YOUR_API_KEY'
BASE_URL = 'https://api.weatherapi.com/v1'

# 過去のデータ
def get_past_weather(location, date):
    url = f"{BASE_URL}/history.json?key={API_KEY}&q={location}&dt={date}"
    return requests.get(url).json()

# 現在のデータ
def get_current_weather(location):
    url = f"{BASE_URL}/current.json?key={API_KEY}&q={location}"
    return requests.get(url).json()

# 未来（予報）のデータ
def get_forecast_weather(location, days=3):
    url = f"{BASE_URL}/forecast.json?key={API_KEY}&q={location}&days={days}"
    return requests.get(url).json()

# 使い方例
print(get_past_weather('Tokyo', '2024-05-01'))
print(get_current_weather('Tokyo'))
print(get_forecast_weather('Tokyo', days=3))