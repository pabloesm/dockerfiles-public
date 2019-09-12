FROM python:3.6.8-slim-stretch

# Setting timezone
RUN apt-get update --fix-missing && \
	apt-get install tzdata && \
	ln -fs /usr/share/zoneinfo/Europe/Madrid /etc/localtime && \
	dpkg-reconfigure -f noninteractive tzdata

# Install some utilities
RUN apt-get update && \
	apt-get install gnupg -y && \
	apt-get install wget -y && \
	apt-get install unzip

# Install Chrome (last stable version)
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - && \
	echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list
RUN apt-get update && \
	 apt-get install -y google-chrome-stable

# Download chromedriver (version 77) and unziped it to a suitable folder
RUN wget https://chromedriver.storage.googleapis.com/77.0.3865.40/chromedriver_linux64.zip && \
	mkdir -p /usr/local/lib/python3.6/site-packages/bin/chromedriver_linux64/ && \
	unzip chromedriver_linux64.zip -d /usr/local/lib/python3.6/site-packages/bin/chromedriver_linux64/ && \
	rm chromedriver_linux64.zip