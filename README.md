To use this example on .net 2.1, run a docker container

docker run -it mcr.microsoft.com/dotnet/sdk:2.1
cd WeatherService
git tag
git checkout PollyService_End
dotnet build
dotnet run&
cd TemperatureService
dotnet build
dotnet run&

curl localhost:5001/weather/celsius/45 # works half of the time
curl localhost:5001/weather/fahrenheit/100 # never works, trips the common circuit breaker

# Wait for CB to get back to half-open
