# server

from socket import AF_INET, SOCK_STREAM, socket
if __name__ == '__main__':
    print ('application started')
    s = socket(AF_INET, SOCK_STREAM)
    print ('TCP Socket created')
    s.bind(('127.0.0.1',7777))
    print ('Socket is bound to %s:%d' % s.getsockname())
    backlog = 0 
    s.listen(backlog)
    print ('Socket %s:%d is in listening state' % s.getsockname())
    client_socket,client_addr = s.accept()
    print ('new client connencted from %s:%d' % client_addr)
    print ('local end-point Socket bound on: %s:%d' % client_socket.getsockname())
    recv_buffer_length = 1024 
    message = client_socket.recv(recv_buffer_length)
    print ('Received %d bytes from %s:%d' % ( (len(message),)+client_addr ))
    print ('Received message: \n%s' % message)
    input('Press Enter To Terminate ...')
    print ('Closed The Client socket')
    s.close()
    print ('Closed The Server Socket')
    print ('Terminating')
