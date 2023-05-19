TARGET = main
TARGET_OBJ = $(TARGET).o
TARGET_LIB = liblg2d.a

CXX = g++

CXXFLAGS = -O3 -march=native -std=c++23 -Wall -Wfatal-errors
CXXLIBS = -pthread 

INC_FOLDER = ./include
SRC_FOLDER = ./src
BUILD_FOLDER = ./build
BIN_FOLDER = ./bin

CXX_OBJECTS = $(BUILD_FOLDER)/test.o 

# compile
$(BUILD_FOLDER)/%.o: $(SRC_FOLDER)/%.cpp $(INC_FOLDER)/%.h 
	$(CXX) -c $(CXXFLAGS) -o $@ $<

#link
$(TARGET): $(TARGET_OBJ) $(CXX_OBJECTS)
	$(CXX) $(CXXFLAGS) $(TARGET_OBJ) $(CXX_OBJECTS) $(CXXLIBS) -o $(TARGET)

#build static library
$(BIN_FOLDER)/$(TARGET_LIB): $(CXX_OBJECTS)
	ar rcs $(BIN_FOLDER)/$(TARGET_LIB) $(CXX_OBJECTS)

#dependencies
main.o: $(BIN_FOLDER)/$(TARGET_LIB)
# $(OBJ_FOLDER)/distance.o: $(OBJ_FOLDER)/primitives.o

clean:
	rm -rf $(CXX_OBJECTS) $(TARGET) $(TARGET_OBJ) $(BIN_FOLDER)/$(TARGET_LIB)
