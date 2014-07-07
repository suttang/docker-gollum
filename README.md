## docker-gollum

This Dockerfile is a simply install gollum.


## Installation

## Usage

### Run container simply

    sudo docker run -d -P --name gollum wamw/gollum
    # Check container port
    sudo docker port gollum
    # 0.0.0.0:49157
    wget http://localhost:49157

### You can attach some options

	sudo docker run -d -P --name gollum wamw/gollum --allow-uploads --live-preview

[github.com/gollum/gollum](https://github.com/gollum/gollum#running)

### Store wikidata at host filesystem

	# Create and initialize wikidata
	mkdir ~/wikidata
	git init ~/wikidata

	sudo docker run -d -P -v ~/wikidata:/root/wikidata wamw/gollum

### Load config file

	# Create and initialize wikidata
	mkdir ~/wikidata
	git init ~/wikidata

	# Create config.rb
	vi ~/config.rb

	sudo docker run -d -P -v ~/wikidata:/root/wikidata wamw/gollum --config /root/wikidata/config.rb

### Use nginx-proxy

	docker run -d -P --name gollum -v ~/wikidata:/root/wikidata -e VIRTUAL_HOST=wiki.example.com -e VIRTUAL_PORT=80 -p 80 wamw/gollum --allow-uploads --config /root/wikidata/config.rb --port 80

[github.com/jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy)






